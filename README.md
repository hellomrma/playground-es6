
**인프런** <https://www.inflearn.com/course/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-es6-%EA%B8%B0%EB%B3%B8>
- 위 인프런 강의를 요약한 내용이며 개인적인 리마인드를 위해 간략하게 정리함

# 자바스크립트 ES6+ 기본
- 섹션 1. let 변수, const 변수 
- 섹션 2. Arrow Function
- 섹션 3. 이터레이션
- 섹션 4. Spread, Rest
- 섹션 5. Destructuring
- 섹션 6. default value
- 섹션 7. for-of 문
- 섹션 8. 연산자, 기타
- 섹션 9. getter, setter
- 섹션 10. Number 오브젝트
- 섹션 11. String 오브젝트
- 섹션 12. Object 오브젝트
- 섹션 13. Template Literal
- 섹션 14. Array 오브젝트
- 섹션 15. Math 오브젝트
- 섹션 16. RegExp 오브젝트
- 섹션 17. Generator 오브젝트
- 섹션 18. Symbol 오브젝트
- 섹션 19. Symbol Property
- 섹션 20. Symbol 함수, 메소드
- 섹션 21. Map 오브젝트
- 섹션 22. WeakMap 오브젝트
- 섹션 23. Set 오브젝트
- 섹션 24. WeakSet 오브젝트

## 섹션 1. let 변수, const 변수

### let
- 블럭 스코프를 가진 변수. 블럭 = {}
- 블럭 {}은 안과 밖이 스코프가 다름 (변수 이름이 같아도 대체되지 않음)
- 초기값은 undefined (var과 다르게 사용할수 없음)
- 콤마를 사용해서 let, var를 함께 할 수 없음
- 블럭 안에서 블럭 밖의 변수는 접근 가능
- 블럭 밖에서 블럭 안의 변수는 접근 불가능
- 같은 스코프에 같은 이름 변수 선언 안됨

### let 변수와 var 변수 차이
for문에서 반복할때 마다
- var 변수를 스코프를 갖지 않음
- let 변수를 스코프를 가짐 (블럭 단위로 관리할 때 사용하면 좋음)

### let 변수와 this
- var 는 window 오브젝트에 설정되지만 let은 그렇지 않음
- let은 script 블럭을 만들고 그 안에 넣음. (내부에서 script 블럭을 만듬)
- this를 찍으면 undefined

### 모든 js 파일상에서 글로벌 obj 사용방법
- var 는 다른파일에서 공유 함
- let 도 다른 파일에서 공유 함 (Script 블럭 안에 들어가 있어서도 공유 됨)
- 블럭 {} 안에 작성할 경우 공유되지 않음.
- 블럭 형태는 Block, Local, Script, Global 4가지 안에 변수가 정의 됨
- 이렇게 다양하게 나뉘진 이유는 권한, 스코프를 나누기 위함

### 호이스팅
아래와 같이 변수를 늦게 설정했음에도 변수값에 접근이 가능한게 호이스팅 (콘솔 찍어보면 undefined)
```javascript
log('music 변수', music);
var music = '음악';
```
let 변수는 호이스팅 불가 (변수 선언을 실행해야지 undefined 할당됨)
블럭{} 안에서 let으로 변수를 설정할시에는 초기 Block 스코프에 할당이 됨 (undefined)

### const
- 값을 바꿀 수 없음
- 반드시 값을 작성. 변수 선언만 불가
- 값을 바꿀 수 없다는건 상수. 상수는 대문자 사용이 관례
- 대신 object 프로퍼티 값을 바꿀수는 있음. 오브젝트 {aaa: 'bbb'}
- 배열의 엘리먼트 값도 바꿀 수 있음

## 섹션 2. Arrow Function
- (param) => {함수코드}
- 단지 기존 function의 축약 형태
- 단 this 참조가 다름
- function은 일반함수 =>는 화살표 함수
- 함수 블럭과 return을 생략한 형태
- 함수 블럭만 작성하게 되면 undefined를 반환
- {key:value}를 소괄호()로 감싸면 {key: value} 반환. 소괄호 감싸지 않으면 undefined 반환
- param 하나일 경우 소괄호 생략 가능
- param 이 없으면 소괄호만 작성

### 화살표 함수 구조, arguments 사용 불가
- prototype에 메소드를 연결하여 확장이 불가 (단독으로 사용해야함)
- 일반 function은 prototype, contructor가 있음
- new 연산자로 인스턴스를 생설할 수 없음

### arguments 사용 불가
- 일반 함수에서는 파라미터 설정하지 않고 값을 넘기면 arguments에 값이 설정됨
- 화살표 함수에서는 referenceError가 발생. 즉 argument 사용 불가
- rest parameter

### 화살표 함수와 this
- use strict 모드에서 함수를 호출할때 일반적으로 함수 앞에 오브젝트 작성은 필수 (window.aaa())
- 대신 화살표 함수는 window 호출하지 않아도 글로벌 오브젝트를 참조함

### 화살표 함수와 인스턴스
- prototype에 화살표 함수를 연결하면 함수 안에서 this가 글로벌 오브젝트를 참조함
- prototype에 일반 함수를 연결하고 함수 안에 화살표 함수를 작성하게 되면 this가 생성한 인스턴스를 참조함

### 화살표 함수 특징
- function 대신 => 를 사용
- 메소드보다 함수로 단독으로 사용하기 위해 만들어짐.
- this는 global 오브젝트를 참조함

## 섹션 3. 이터레이션
- 이터레이션 : 반복
- for문의 반복 개념과 차이가 있음
- Symbol.iterator를 사용해서 하나씩 확인할 수 있음
- 이터레이션을 위한 프로토콜이 필요 (오브젝트가 이터레이션 할수 있는 구조여야함)
- 이터러블, 이터레이터

### 이터러블 프로토콜
- 오브젝트가 반복할 수 있는 구조여야 함
- Symbol.iterator 를 가지고 있어야 함

### 이터러블 오브젝트
- 이터러블 프로토콜을 갖고 있는 오브젝트

### 이터레이터 프로토콜
- 값을 순서대로 생성하는 방법
- next()가 있음
- 이터레이터라고도 부름
- {value: 10, done: false} done: false는 이터레이터 상태
- 값이 없으면 undefined, done: true 나옴

## 섹션 4. Spread, Rest
- let 변경할 수 있다
- const 변경할 수 없다

### spread
- 구문 : [...iterable]
- 점 3개를 작성하고 이어서 이터러블 오브젝트 작성

### Array spread
- spread 대상 배열을 작성한 위치에 엘리먼트 단위로 분리(전개)
- 값이 대체되지 않고 전개됨
```javascript
const one = [11, 12];
const result = [11, 12 ...one];
console.log(result);
// [11,12,11,12]
```

### String spread
- 대상 문자열을 작성한 위치에 문자 단위로 전개
```javascript
const target = "ABS";
console.log(target);
// [A,B,C]
```

### Object spread
- spread 대상 Object를 작성한 위치에 프로퍼티 단위로 전개
- 프로퍼티 이름이 같으면 대체 됨

### push(...spread)
- 배열 끝에 분리하여 전개됨

### Rest 파라미터
- function(param, paramN, ...name)
- 분리하여 받은 파라미터를 배열로 결합 spread = 분리, rest = 결합
- 위 마지막 ...name의 경우 나머지 값을 결합하기 때문에 rest 파라미터라고 함

### function spread
- 호출하는 함수의 파라미터에 spread 대상 작성
- 함수가 호출되면 우선 파라미터 배열을 엘리먼트 단위로 전개하고 파라미터 값으로 넘겨줌
- 호출받는 함수의 파라미터에 순서대로 매핑됨

### Array-like
- Object 타입이지만 배열처럼 이터러블 가능한 오브젝트
- for 문으로 전개 할수 있음 (length 프로퍼티는 전개되지 않음. for~in 문으로 전개하면 length 프로퍼티도 전개됨)
- 프로퍼티 값을 0부터 1씩 증가해야하고 length에 전체 프로퍼티 수 작성해야함
```javascript
const values = {0:'a', 1:'b', 2:'c', length: 3}
for (let k=0; k<values.length; k++>){
	console.log(values[k])
}
// 가
// 나
// 다
```

## 섹션 5. Destructuring
- 분할 할당
- 사전적 의미 : 구조를 파괴하다
```javascript
let one,two,theree;
const list=[1,2,3];
[one,two,theree] = list
console.log(one,two,three, list);
// 1,2,3,[1,2,3]
```

### Array 분할 할당
- 인덱스에 해당하는 변수에 할당함
- 할당할 수 없는 변수의 경우 undefined
```javascript
let one, two, three, four;
[one, , ,four]=[1,2,3,4];
console.log([one,two,three,four]);
// 1,undefined, undefined, 4]
```

### Object 분할 할당
- Object의 프로퍼티를 분할하여 할당
- 이름이 같은 프로퍼티에 값을 할당

## 섹션 6. default value
- 테스트

## 섹션 7. for-of 문
## 섹션 8. 연산자, 기타
## 섹션 9. getter, setter
## 섹션 10. Number 오브젝트
## 섹션 11. String 오브젝트
## 섹션 12. Object 오브젝트
## 섹션 13. Template Literal
## 섹션 14. Array 오브젝트
## 섹션 15. Math 오브젝트
## 섹션 16. RegExp 오브젝트
## 섹션 17. Generator 오브젝트
## 섹션 18. Symbol 오브젝트
## 섹션 19. Symbol Property
## 섹션 20. Symbol 함수, 메소드
## 섹션 21. Map 오브젝트
## 섹션 22. WeakMap 오브젝트
## 섹션 23. Set 오브젝트
## 섹션 24. WeakSet 오브젝트
