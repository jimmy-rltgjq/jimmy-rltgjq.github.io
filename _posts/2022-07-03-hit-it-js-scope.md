---
layout: post
title: "[때려챠라] JS/Scope"
category: fuckoff
---

### Scope란?
|  프로그래밍에서 사용되는 변수들의 사용 가능 범위


### 스코프 범위 종류

**글로벌 스코프 / Global Scope**
    
| 코드 어드곳에서나 참조 가능


**로컬 스코프 / Local Scope**

| 선언된 함수와 하위 함수에서만 참조 가능

**Scope Example**
```javascript
// 글로벌 번수
var global_scope = 'global_variable'; 

function local_function(){
    // `local_function` 함수의 로컬 변수
    var local_scope = 'local_variable'; 
    
    console.log(local_scope);

    function sub_function(){
        // `sub_function` 함수의 로컬 변수
        var local_sub_scope = 'local_sub_variable'; 
        console.log(global_scope);
        console.log(local_scope);
    }

    // 에러 발생 - 현재 스코프 위치 = local_function
    console.log(local_sub_scope) 
}

function local_function2(){
    var local_scope_2 = 'local_variable2';
    
    console.log(global_scope);
    console.log(local_scope); // 에러 발생
    console.log(local_scope_2);
}
```


- 글로벌 스코프는 글로벌 스코프에 선언되어서 모든 함수에서 사용가능함
- 지역 변수들은 선언된 함수 혹은 그안에서 생성한 함수에서만 사용가능함

### 렉시컬 스코프
| 함수의 실행 위치가 아닌 선언된 위치에 따라 스코프가 결정되는 것

Code Example
```javascript
var global = 'global_variable';

function first() {
  var global = 'changed_global_variable';
  bar();
}

function second() {
  console.log(global);
}

first(); 
second(); 
```

- 위 코드를 실행 하면 `global_variable` 문자가 두번 콘솔에 출력된다.
- first 함수에서 변경한 global 변수는 해당 함수 안에서만 영향을 받는다.
- 만약 second 함수가 first 함수 안에 선언 되어서 실행하면 second에서 사용하는 global 변수를 변경 할 수 있다.
