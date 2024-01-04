# hyeyomi-js-algorithm

- [패스트캠퍼스 프론트엔드 초격차 패키지](https://fastcampus.co.kr/dev_online_fesignature) 中 Course 3, JavasScript로 끝내는 자류구조/알고리즘 강의를 듣고 작성하는 강의 노트입니다. 
- 대표 알고리즘의 기본형을 정리할 예정입니다.

## Intro
- 빈도가 높은 알고리즘 유형에는 '구현', 'DFS/BFS(탐색)', '탐욕' 알고리즘 유형이 출제 빈도가 높은 편이다.
- 코딩테스트 대비 : 알고리즘 유형 별로 이론 및 핵심 문제를 10개 이상 풀어보기. (수학 공부와 크게 다르지 않은 걸?)
- 알고리즘 문제 난이도는, 컴퓨터공학 학부 과정에서 배우는 기초 내용 정도이다. 
- 원하는 기업의 기출 문제를 푸는 것도 중요하다.


## 01. 코딩 테스트 알아보기
### 시간 복잡도 : 알고리즘의 성능을 나타내는 척도
- 특정 크기의 입력에 대하여 알고리즘의 수행 시간을 분석
- 값이 크게 증가하는 정도
- 복잡도가 낮을수록 우수함. (알고리즘이 빠르게 동작해서 결과가 금방 나옴)

### 빅오 표기법(Big-O Notation)
- 가장 빠르게 증가하는 항을 고려하는 표기법
- 함수의 상한을 나타냄
- 예시) 연산 횟수가 3N<sup>3</sup> + 5N<sup>2</sup> + 1,000,000 인 알고리즘이 있다고 가정. N이 증가하면 3N<sup>3</sup>을 제외한 다른 항의 영향력은 작아진다.
- Big-O 표기법에서는 차수가 가장 큰 항에서 계수를 제외한다. 최종 결과은 **O(N<sup>3</sup>)**

#### 시간 복잡도의 종류
![big-o](https://raw.githubusercontent.com/Anne-Hyeyeon/hyeyomi-js-algorithm/main/assets/big-o-example.png)

1) 상수 시간 - 사칙연산.
2) 로그 시간 - 로그는 값을 **빠르게** 줄여 준다. 이분 탐색.
3) 선형 시간 - 배열이 있을 때, 배열의 원소를 확인해서 찾고자 할 때 사용.
4) 로그 선형 시간 - 정렬 알고리즘(병합 정렬, 힙 정렬 등)
5) 이차 시간 
6) 삼차 시간 
7) 지수 시간
* 아래로 갈수록 좋지 않은 알고리즘이라고 할 수 있다.

### 알고리즘 설계시 고려할 점
- 일반적인 CPU 기반 컴퓨터에서, JS를 기준으로 1억 번의 연산을 처리하기 위해서 약 1~5초의 시간이 소요됨.
- 이런 경우, O(N<sup>3</sup>)의 알고리즘을 설계한 경우, N 값이 5,000이 넘으면 약 125억 정도가 나오고 100초 이상이 소요된다.
- 문제에서 가장 먼저 확인해야 하는 내용은 바로 **시간 제한**이다.

#### 요구사항에 따라 적절한 알고리즘 설계하기
**시간 제한이 1초인 문제를 만났을 때**
1) N의 범위가 500인 경우 : 시간 복잡도가 O(N<sup>3</sup>)인 알고리즘 설계하면 문제를 풀 수 있다.
2) N의 범위가 2,000인 경우 : 시간 복잡도가 O(N<sup>2</sup>)인 알고리즘을 설계하면 문제를 풀 수 있다.
3) N의 범위가 100,000인 경우 : 시간 복잡도가 O(NlogN)인 알고리즘을 설계하면 문제를 풀 수 있다.
4) N의 범위가 10,000,000인 경우 : 시간 복잡도가 O(N)인 알고리즘을 설계하면 문제를 풀 수 있다.

### 알고리즘 코딩 테스트 문제의 입출력 형식
1. 1단계 - 데이터를 입력 받거나 생성함.
2. 2단계 - 이후 적절한 알고리즘을 사용하여 도출된 정답을 정확한 형식으로 출력.
- ex) N명의 학생의 데이터가 **주어졌을 때**, 이를 내림차순 정렬한 **결과를 출력**하여라.

### N명의 학생의 데이터가 주어졌을 때, 이를 내림차순 정렬한 결과를 출력하여라.
- 입력 형식 : 첫 번째 줄에는 학생수 N이 자연수로 주어지고, 둘째 줄에 공백을 기준으로 하여 N명의 학생에 대한 성적이 정수 형태로 주어진다.
  (2 <= N <= 1000, 0 <= 성적 <= 100)
- 출력 형식 : N명의 학생의 성적을 내림차순 정렬한 결과를 첫째 줄에 공백을 기준으로 구분하여라.

* 입출력 형식에 맞추는 게 핵심. 요구사항을 꼼꼼히 파악하는 게 중요하다.


### 입력과 출력
#### 기본 출력
- 일반적인 알고리즘을 풀 때, 표준 출력으로 console.log()를 이용한다.
```js
// 단순히 문자열을 출력한다.
console.log('Hello World!');

result = 35;
// 템플릿 리터럴을 사용해 문자열 내부에 변수를 포함.
console.log(`정답은 ${result}입니다.`);
```

##### Javscript 기본 사칙 연산 관련 Tip
- parseInt(a/b)를 할 경우, 몫만 남는다.

#### JS 빠른 출력
- JS로 코딩 테스트 문제를 풀 때, 출력 과정만으로 시간 초과를 받을 때가 있다.
- 출력 시간을 단축하기 위해 다음과 같은 방법을 유용하게 사용할 수 있다. -> 한꺼번에 뭉쳤다가 출력
- 단, 메모리는 더 많이 사용된다.

  ```js
  let answer = '';

  /*
  여러 출력 결과를 하나씩 출력할 때 매번 console.log()를 실행하지 않는다.
  하나의 문자열에 결과를 저장한 후, 한 번에 출력하는 게 더 효율적이다.
  */

  for (let i = 1; i <= 100; i++) {
    answer += i + '`\n`; // 문자열로 변환하여 기록
  }

console.log(answer);

#### 기본 입력 - fs 모듈
- 입력 데이터가 텍스트 파일 형태로 주어지는 경우, 파일 시스템 모듈을 사용함.
- 예시) 전체 텍스트를 읽어온 뒤, 줄바꿈 기호를 기준으로 구분하여 리스트로 변환.
```js
// readline 모듈보다는 fs를 이용하는 게 좋다.
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');
// let input = fs.readFileSync('input.txt').toString().split('\n');

console.log(input);
```

#### fs 모듈을 사용할 수 없는 경우- readline 모듈
```js
// readline 객체 만들기
const rl = require('readline').createInterface({
  input: process.stdin, // 표준 입력을 받는다. (한 줄 한 줄 키보드 입력을 이용해 명령을 한다.)
  output: process.stdout  // 표준 출력
});

let input = [];

rl.on('line', function(line) {
  // 콘솔 입력 창에서 줄바꿈(Enter) 입력할 때마다 호출
  input.push(line);
}).on('close', function() {
  console.log(input);
  process.exit();
});
```


## 02. 코딩 테스트를 위한 자바스크립트 기본 문법 
### for 반복문
* 조건에 따라 특정한 코드를 반복하고자 할 때 사용할 수 있는 코드.

- 형태
```js
for (초기물; 조건문; 증감문) {
  // statements
}
```

###  while 반복문
- 형태
```js
/*
블록 내부의 코드가 실행되기 전의 참 혹은 거짓을 판단함.
*/

while(조건문) {
  // 실행되는 코드 부분
}
```
###  Number와 String 형태 변환
```js
let a = "777";
let b = Number(a);
console.log(b); // 77

let a = 777;
let b = String(a);
console.log(b) : // '777'
```

### Array.prototype.reduce()
* 원소에서 가장 큰 값 / 작은 값 찾기
* 배열의 모든 원소에 대해 특정한 연산을 순차적으로 사용.

```js
/*
reduce() 메서드는 배열의 각 요소에 대해, reducer 함수를 실행한 뒤 하나의 결과를 반환함.

리듀서 : (accumulator, currentValue) => (반환값)

- 배열의 각 원소를 확인하여, 원소를 currentValue에 저장
- 반환값은 그 이후 원소에 대해 accumulator에 저장
*/

let data = [5, 2, 9, 8, 4]

// minValue 구하기
let minValue = data.reduce((a, b) => Mate.min(a,b));

// 원소의 합계 구하기
let summary = data.reduce((a, b) => a + b)
console.log(summary); // 28
```

### 배열 초기화
- 알고리즘 문제를 풀 때 사용되는 배열 초기화 방식

1) 직접 초기화
```js
let arr = [1, 2, 3, 4, 5];
```

2) new Array와 fill을 이용한 초기화
- new Array(원소 개수)한 다음 그것들을 0으로 채운다.
```js
// 길이가 5이고 모든 월소의 값이 9인 배열 초기화
let arr = new Array(5).fill(0);
```

### 집합 자료형
- 특정한 원소의 등장 여부를 파악할 때 집합 자료형을 효과적으로 사용할 수 있다.

```js
let mySet = new Set(); //집합 객체 생성

// 여러 개의 원소 삽입
mySet.add(3);
mySet.add(5);
mySet.add(7);
mySet.add(3);

console.log(`원소의 개수: ${mySet.size}`);
console.log(`원소 7 포함여부: ${mySet.has(7)}`);

// 원소 5 제거
mySet.delete(5);

// 원소 하나씩 출력
for (let item of mySet) console.log(item);
```

### 소수점 아래 특정 자리에서 반올림
* 실수를 출력할 때 소수점 아래 특정 자리에서 반올림
```js
// 특정 실수에 대하여 toFixed()를 이용해 소수점 아래 둘째 자리까지 출력
let x = 123.456
console.log(x.toFixed(2))
```
- toFixed 안에서는 반올림하고자 하는 소수점의 위치

### 이스케이프 시퀀스
- 예약 문자 혹은 특수문자를 출력하기 위한 이스케이프 시퀀스

|시퀀스|문자|
|---|---|
| \t | 탭 |
| \\ | 역 슬래시 |
| \" | 큰 따옴표 |
| \' | 작은 따옴표 |


## 03. JavaScript 입출력 문제 풀이 
### A+B
#### 링크 : https://www.acmicpc.net/problem/1000
#### 문제 : 두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.
#### 핵심 아이디어
- JavaScript를 이용해 **정수**를 처리한다.
- 입력 받은 문자열 데이터를 정수로 변환한다.
- 이후, 덧셈을 수행한 결과를 출력한다.
- `fs 모듈`을 이용해 특정 파일에서 문자열을 읽어올 수 있다.

```js
// fs 모듈을 이용해 파일 전체를 읽어온다. 그 후, 문자열로 저장한다.
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// ["1", "2"] (각각의 배열에 문자열이 담기게 한다.)
let line = input[0].split(' ');

let a = parseInt(line[0]); // 1
let b = parseInt(line[1]); // 2

console.log(a + b);
```

#### 분석 
1. 파일 시스템 모듈 불러오기
```js
let fs = require('fs');
```
- node.js의 시스템 모듈인 js을 불러온다. 이를 이용하면, **파일을 읽거나 쓸 수 있다**. 위 코드 문제의 경우, fs는 표준 입력을 읽기 위해 사용된다. (요약 : fs를 불러오면 파일을 읽거나 쓸 수 있게 된다.)
- 결과물 : fs 모듈이 메모리에 로드됨.

2. 표준 입력 읽기.
```js
let input = fs.readFileSync('/dev/stdin').toString().split('\n'); 
```
#### /dev/stdin 이란?
- UNIX 또는 UNIX 계열 운영 체제 (Linux, macOS)에서 사용되는 특별한 파일 시스템 경로이다.
- 실제 파일이 아닌, 파일 시스템의 특수한 경로다.
  프로그램 이 경로에서 데이터를 받았을 경우, 실제로는 사용자가 키보드로 입력하거나 파이프(`|`)나 리디렉션 (`<`)을 통해 다른 프로그램, 외부로부터 전송된 파일 받음.
- `표준 입력`을 나타내고, 프로그램이 사용자나 다른 프로그램으로부터 **입력 받을 때** 사용된다.
- stdin은 `standard input`의 약자.

3. 첫 번째 줄 처리:
```js
let line = input[0].split(' ');
```
- `input`배열의 첫 번째 요소를 공백 문자로 분리하여 `line`배열에 저장한다. 이 경우, `line`배열은 두 개의 문자열을 담게 된다.

4. 문자열을 숫자로 변환
```js
let a = parseInt(line[0]);
let b = parseInt(line[1]);
````
- `parseInt`함수를 사용해 `line`배열의 요소를 정수로 변환. (Number도 가능). 변환된 값을 a,b 변수에 저장함.

5. 결과 출력
```js
console.log(a+b);
```

### 사칙 연산
#### 링크 : https://www.acmicpc.net/problem/10869
#### 내가 만든 답 (오답)
```js
let fs = require('fs');

let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let line = input[0].split(' ');

let A = Number(line[0]);

let B = Number(line[1]);

console.log(A + B);
console.log(A - B);
console.log(A * B);
console.log(A / B);
console.log(A % B);
```

### 정답
```js
let fs = require('fs');

let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let line = input[0].split(' ');

let A = Number(line[0]);

let B = Number(line[1]);

console.log(A + B);
console.log(A - B);
console.log(A * B);
console.log(Math.floor(A / B)); // 나눗셈 결과를 정수로 반환
console.log(A % B);
```

### 오답 풀이
- JavaScript에서 / 연산자는 실수 나눗셈을 수행하므로, 결과가 항상 실수(소수점이 있는 숫자)로 반환된다.
- 문제에서 자연수 나눗셈의 결과를 요구하는 경우, 결과를 자연수로 변환할 필요가 있다.

### 다른 정답
```js
var i = require('fs').readFileSync('/dev/stdin').toString().split(' ').map(function(e) { return parseInt(e); });
console.log(i[0] + i[1]);
console.log(i[0] - i[1]);
console.log(i[0] * i[1]);
console.log(Math.floor(i[0] / i[1]));
console.log(i[0] % i[1]);
```
