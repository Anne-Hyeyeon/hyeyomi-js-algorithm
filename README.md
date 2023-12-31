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

// minVal원소의 값이 9인 배열 초기화
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
#### 오답
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

#### 정답
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

#### 오답 노트
- JavaScript에서 / 연산자는 실수 나눗셈을 수행하므로, 결과가 항상 실수(소수점이 있는 숫자)로 반환된다.
- 문제에서 자연수 나눗셈의 결과를 요구하는 경우, 결과를 자연수로 변환할 필요가 있다.

#### 다른 정답 (추후 분석)
```js
var i = require('fs').readFileSync('/dev/stdin').toString().split(' ').map(function(e) { return parseInt(e); });
console.log(i[0] + i[1]);
console.log(i[0] - i[1]);
console.log(i[0] * i[1]);
console.log(Math.floor(i[0] / i[1]));
console.log(i[0] % i[1]);
```


### 다른 사람 풀이에서 본 팁
#### 구조 분해 할당
```js
const [A, B] = fs.readFileSync("/dev/stdin").toString().trim().split('\n');
const [B0, B1, B2] = B.split('');
```
입력을 통해 받은 값을, 바로 배열에 할당할 수 있다.

#### 문자 배열
- 자바스크립트에서 문자열은 일종의 "문자 배열"처럼 동작하며, 특정 인덱스에 위치한 문자에 배열처럼 접근할 수 있다. (이는 문자열이 '문자의 배열'로 취급되기 때문에 가능한 동작임.)
- 예를 들어, 문자열 str이 "hello"라면, str[0]은 'h', str[1]은 'e'와 같이 각 문자에 접근할 수 있다. 이러한 특성 덕분에 문자열에서 개별 문자를 추출할 때 split('') 메서드를 사용하지 않고도 직접 인덱스를 통해 접근할 수 있다.
```js
let str = "hello";
console.log(str[0]); // 'h'
console.log(str[1]); // 'e'
console.log(str[2]); // 'l'
// 등등...
```

## JavasScript 조건문 문제 풀이
### 시험 성적
#### 링크 : https://acmicpc.net/problem/9498
#### 오답
```js
let fs = require('fs')
let input = fs.readFileSync('/dev/stdin').toString();
let score = parseInt(input);

const getGrade = (score) => {
    if(90<=score<=100) return 'A';
    if(80<=score<=89) return 'B';
    if(70<=score<=79) return 'C';
    if(60<=score<=69) return 'D';
    return 'F';
}

console.log(getGrade(score));
```
#### 오답 노트 
- 자바스크립트에서 연속적 비교 연산자를 사용하면, 기대한 대로 작동하지 안흔ㄴ다.
- 자바스크립트에서 연속 비교는 두 부분으로 나누어 평가된다.

#### 수정한 정답
```js
let fs = require('fs')
let input = fs.readFileSync('/dev/stdin').toString();
let score = parseInt(input);

const getGrade = (score) => {
    if (score >= 90 && score <= 100) return 'A';
    if (score >= 80 && score <= 89) return 'B';
    if (score >= 70 && score <= 79) return 'C';
    if (score >= 60 && score <= 69) return 'D';
    return 'F';
}

console.log(getGrade(score));
```
- 참고로 `else if문`을 써도 동일하게 동작한다. else if문의 경우, 이전 조건들이 모두 거짓일 때만 평가된다.

### 알람 시계
#### 링크 : https://acmicpc.net/problem/2884
#### 핵심 아이디어
1. 현재 시간이 주어졌을 때, 45분을 감소시킨다.
2. 0분보다 작아지면, hour 1 감소
3. 0시보다 작아지면, min 23시로 초기화.
- **문제 풀기 전 핵심 아이디어 확인하기**

#### 정답
```js
let fs = require("fs");

const input = fs.readFileSync("/dev/stdin").toString().split(" ");

const inputHour = Number(input[0]);
const inputMin = Number(input[1]);

const getAlarmTime = (inputHour, inputMin) => {
  let resultHour = inputHour;
  let resultMin = inputMin - 45;

  if (resultMin < 0) {
    resultMin += 60;
    resultHour -= 1;
  }

  if (resultHour < 0) {
    resultHour = 23;
  }

  return console.log(resultHour, resultMin);
};

getAlarmTime(inputHour, inputMin);
```

### 오븐 시계
#### 링크 : https://www.acmicpc.net/problem/2525
#### 핵심 아이디어
 1. 훈제오리구이를 시작하는 시각과 오븐구이에 필요한 시간을 입력으로 받는다.
 2.  이들을 분 단위로 계산하여 최종 시각을 구한다.
 3.  여기서 totalMinutes를 사용하여 현재 시각과 필요한 시간을 더하고, 이를 24시간 형식에 맞게 조정한다.

#### 정답 
```js
let fs = require('fs');

let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let [hour, min] = input[0].split(' ').map(Number);

let time = Number(input[1])

let getTransferredTime = hour * 60 + min + time;

let resultHour = parseInt(getTransferredTime / 60) % 24;

let resultMin = getTransferredTime % 60;

console.log(resultHour, resultMin);
```

#### 해설 속 정답
```js
const fs = require('fs');
const input = fs.readFileSync('/dev/stdin').toString().split('\n');

let [hour, minute] = input[0].split(' ').map(Number);
let time = Number(input[1]);

let totalMinute = hour * 60 + minute + time;
// 총 분을 1440분(24시간)으로 나눈 나머지를 구하여 하루를 초과하는 시간 처리. 
totalMinute %= 1440;
hour = parseInt(totalMinute / 60);
minute = totalMinute % 60;

console.log(hour + ' ' + minute)
```
- `totalMinute`는 현재 시각을 분으로 환산한 값.
- 1440은 하루의 총 분을 나타냄.
- totalMintue %= 1440은, totalMinutes을 1440으로 나눈 나머지를 구하는 연산임. 결과값은 **0부터 1439**이다.
- 이는 하루를 넘어가는 시간을 다시 0시 0분부터 시작하는 24시간 형식으로 재설정함.
- **%으로 얻은 값이 가질 수 있는 범위는, 대상보다 1 적은 값**
- 시간 계산에서, 단위 관련 문제를 풀 때 유용!

#### 구조 분해 할당과 map으로 코드 길이를 짧게 해보기.
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin'.toString().split('\n');

let [a, b] = input[0].split(' ').map(Number);
let c = Number(input[1]);
```

#### 시간 문제 관련 정보
- 1440 : 하루는 24시간, 각 시간은 60분. 따라서 하루는 총 1440분
- hour에다가 60을 곱해 분 형태로 만든 숫자는, 시간 계산에서 하루가 넘어간 시간을 처리하는 데 사용된다.
- 몫 구하기 : Math.floor 또는 parseInt


### 주사위 세 개
#### 링크 : https://www.acmicpc.net/problem/2480
#### 핵심 메서드와 문법
- `Set` 객체 사용 : `Set`은 중복을 허용하지 않는 데이터 구조로, 배열에 있는 모든 중복 원소를 자동으로 제거한다.
```js
let numbers = [1, 2, 2, 3, 4, 4, 5, 5];

let uniqueNumbers = [...new Set(numbers)];

console.log(uniqueNumbers); // [1, 2, 3, 4, 5]
```
- new Set(numbers)는 numbers 배열의 모든 중복 원소를 제거하여 Set 객체를 생성한다. 그리고 스프레드 연산자 ...를 사용하여 이 Set 객체를 다시 배열로 변환.
- Math.Max(Array) : 배열 원소 중 가장 큰 값
- Math.abs(Number) : 절대값 구하기
- 두 개가 같은 숫자 찾기


#### 오답
```js
const fs = require('fs');

const numbers = fs.readFileSync('/dev/stdin').toString().split(' ').map(Number);

const [a, b, c] = numbers;

const maxNumber = Math.max(...numbers);

const uniqueNumbers = [...new Set(numbers)];

if (uniqueNumbers.length === 1) {
    console.log(10000 + a * 1000);
}

else if (uniqueNumbers.length === 2) {
    console.log(1000' + (Math.abs(a-b-c) * 100));
}
         
else console.log(maxNumber * 100);
```
- uniqueNumbers는 배열이므로 배열의 길이를 비교해줘야 한다.
- Math.abs(a-b-c)는 내가 의도한 대로 동작하지 않을 것이다. (바보)


### 정답
```js
const fs = require("fs");

const numbers = fs.readFileSync("/dev/stdin").toString().split(" ").map(Number);
const [a, b, c] = numbers;

const uniqueNumbers = [...new Set(numbers)];

if (uniqueNumbers.length === 1) {
  console.log(10000 + a * 1000);
} else if (uniqueNumbers.length === 2) {
  let sameNumber = a === b ? a : a === c ? a : b;
  console.log(1000 + sameNumber * 100);
} else {
  let maxNumber = Math.max(...numbers);
  console.log(maxNumber * 100);
}
```
- 애초부터 a,b,c를 비교해가는 게 훨씬 더 효율적일 수도. (굳~이 set을 만들 필요가 없다.)



## JavaScript 반복문 문제 풀이
### 합 (sum)
#### 링크 : https://www.acmicpc.net/problem/8393
#### 문제 : 1부터 n까지 합을 출력한다.

#### 문제풀이 1 
##### 핵심 아이디어
1. 자연수 N의 최대 값은 10,000이다.
2. 따라서, 단순히 1부터 10,000까지의 값을 차례도 더해도 괜찮다.
3. 이 경우 시간 복잡도가 O(N)이다.

##### 풀이
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString();

let n = Number(input[0]);
let summary = 0;

for (let i - 1; i <= n; i++) {
  sommary += i;
}

console.log(summary);
```
- 문자열을 수로 변환할 때, parseInt에 비하여 Number의 속도가 더 빠르게 동작.


#### 문제풀이 2
##### 핵심 아이디어
1. 단순히 등차수열의 합 공식을 이용할 수 있다.
2. 등차수열의 1항부터 제 N항까지의 합을 S<sub>n</sub> 이라고 하자.
3. 첫째 항이 a, 마지막 항이 l일 때: S<sub>n</sub> = N(a + l)/2

##### 풀이
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString();

let  = Number(input[0]);

// 등차수열의 합 공식
console.log(n * (n + 1) / 2);
```

#### 문제풀이 3
##### 핵심 아이디어 
- 배열 생성하기
- reduce 메서드로 누적 합 구하기

##### 풀이
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString();

let n = Number(input[0]);

// Array.from 메서드를 사용하여 1부터 n까지의 숫자 배열을 생성
let numbers = Array.from({length: n}, (_, i) => i + 1);

// 배열의 reduce 메서드를 사용하여 모든 숫자를 더함
let summary = numbers.reduce((acc, num) => acc + num, 0);

console.log(summary);
```
- Array.from({length: n}, (_, i) => i + 1): 이 부분은 길이가 n인 배열을 생성하고, 각 요소를 1부터 n까지의 숫자로 초기화함.
- reduce((acc, num) => acc + num, 0): reduce 메서드는 배열의 각 요소에 대해 주어진 리듀서(reducer) 함수를 실행하고, 하나의 결과값을 반환.

### 구구단
#### 링크 : https://www.acmicpc.net/problem/2739
#### 문제 : N을 입력받은 뒤, 구구단 N단을 출력하는 프로그램을 작성하시오. 출력 형식에 맞춰서 출력하면 된다.
#### 정답 
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let number = Number(input[0]);

let numbers = Array.from({ length: 10 }, (_, i) => i);

let summary = numbers.reduce((_, num) =>
  console.log(`${number} * ${num} = ${number * num} `)
);
```
- reduce 대신 forEach 사용 가능.

#### 해설 속 정답
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);

for (let i = 1; i <= 9; i++){
  console.log(`${n} * ${i} =  ${n * i}`);
}
```


### 별 찍기
#### 링크 : https://www.acmicpc.net/problem/2438
#### 문제 : 첫째 줄에는 별 1개, 둘째 줄에는 별 2개, N번째 줄에는 별 N개를 찍는 문제
#### 정답
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);

// n만큼의 길이를 가진 배열을 생성하고, 각 줄에 대한 별을 찍는다.
Array.from({ length: n }, (_, i) => console.log("*".repeat(i + 1)));
```

- 처음에, Array.from({ length: n }, callback)을 사용하여 길이가 n인 배열을 생성한다. 배열의 각 요소는 undefined가 된다.
- JavaScript에서 Array.from 메서드를 사용하면, 배열의 각 요소에 대해 콜백 함수를 실행한다.
- 이 콜백 함수 내에서 console.log를 호출하면, 배열의 각 요소에 대해 console.log가 실행되어 결과를 콘솔에 출력한다.
- 따라서 console.log("*".repeat(i + 1))는 각 줄에 i + 1개의 별을 출력한다.
- repeat() 메서드는 문자열을 주어진 횟수만큼 반복하여 새 문자열을 생성한다.

#### 다른 방법
```js
// 길이가 n인 배열을 생성하고 초기화
let arr = Array.from({ length: n });

// forEach를 사용하여 각 요소에 대해 함수를 실행
arr.forEach((_, i) => console.log("*".repeat(i + 1)));
```

### 빠른 A+B
#### 링크 : https://www.acmicpc.net/problem/15552
#### 문제 : 첫 줄에 테스트케이스의 개수 T가 주어진다. T는 최대 1,000,000이다. 다음 T줄에는 각각 두 정수 A와 B가 주어진다. A와 B는 1 이상, 1,000 이하이다. 각 테스트케이스마다 A+B를 한 줄에 하나씩 순서대로 출력한다.
#### 오답
```js
let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().split("\n");

let caseNum = Number(input[0]);

Array.from({ length: caseNum }).forEach((_, i) => {
  let [a, b] = input[i + 1].split(" ").map(Number);
  console.log(a + b);
});
```
- 원인 : 시간 초과

#### 핵심 아이디어
1. 문자열 변수에 정보를 담은 뒤 한꺼번에 문자열 출력.

#### 해설 속 정답
```js
let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().split("\n");

let testCase = Number(input[0]);
let answer = '';

for (let t = 1; t <= testCase; t++);{
  let data = input[t].split(' ');
let a = Number(data[0]);
let b = Number(data[1]);
answer += a + b + '\n';
}

console.log(answer);
```

#### readline
- Node.js에서 대량 데이터 처리를 위해서는 `fs.readFildSync`와 같은 동기식 입출력 대신, 스트림을 사용하는 게 좋다.
- `스트림` : 데이터를 작은 조각으로 나누어 처리함.
```js
let fs = require("fs");
let readline = require("readline");

let rl = readline.createInterface({
    input: fs.createReadStream("/dev/stdin"),
})

let lines = [];

rl.on('line', (line) => {
  lines.push(line);
}).on('close', () => {
  let results = lines.slice(1) 
    .map(line => line.split(' ').map(Number))
    .reduce((acc, [a, b]) => acc + (a + b) + "\n", "");

  console.log(results);
});
```

## JavaScript 배열 문제 풀이
### 최소, 최대
#### 링크 : https://www.acmicpc.net/problem/10818
#### 오답
```js
let fs = require("fs");

let input = fs.readFileSync("/dev/stdin").toString().split("\n");

let number = Number(input[0]);

let arr = Array.from({ length: number }, () => input[1].map(Number));

let answer = `${Math.min(arr)} ${Math.max(arr)}`;

console.log(answer); // NaN NaN
```

- input(1).map(Number)의 사용 : `input[1]`은 문자열이다. 따라서 `.map(Number)`를 직접 사용할 수 없다. 대신, 문자열을 공백 기준으로 분할한 후 map(Number)를 사용해야 한다.
- Array.from 의 사용법 : Array.from은 기본적으로 array-like object(문자열, nodeList, arguments)를 배열로 만드는 데 사용된다. 
- Math.max와 Math.min의 사용법 : 배열 내 요소를 확인하는 경우 스프레드 연산자 사용해야 함.

#### 다른 사람의 풀이
```js
let a = require("fs").readFileSync("/dev/stdin", "utf8").split("\n")[1].split(' ')
console.log(Math.min(...a), Math.max(...a))
```
- 숫자의 개수를 가져올 필요도 없다. 바로 배열 내 요소를 Math.min과 Math.max를 이용해서 비교할 수 있음.

#### 해설 풀이 1
##### 핵심 아이디어
1. 배열의 원소를 **하나씩 확인**하여, 최댓값과 최솟값을 찾는다.
2. 최댓값과 최솟값 정보를 업데이트한다.
- 배열을 순회(iterate)함으로써 값을 구할 수 있음.
- 원소를 하나씩 확인할 경우, 시간 복잡도 O(N)으로 확인할 수 있음.

```js
let fs = require('fs');

let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let arr = input[1].split(' ').map(Number);

/*
모든 정수는 -1,000,000보다 크거나 같고,
1,000,000보다 작거나 같은 정수이다.
*/

let minValue = 1000001; // 일단 큰 수로 초기화
let maxValue = -1000001; // 일단 작은 수로 초기화

for (let i = 0; i < n; i++) {
  if (minValue > arr[i]) minValue = arr[i];
  if (maxValue < arr[i]) maxvalue = arr[i];
}

console.log(minValue, maxValue);
```

#### 해설 풀이 2
```js
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let data = input[1].split(' ').map(x => Number(x));

let minValue = data.reduce((a, b) => Math.min(a, b));
let maxValue = data.reduce((a, b) => Math.max(a, b));

console.log(minValue + " " + maxValue);
```
- `reduce`함수가 `data`배열의 각 요소에 대해 콜백 함수인 `(a,b) => Math.min(a,b)`를 실행한다.
- a는 누적값, b는 현재 배열 요소
- `Math.min(a,b)는 a와 b중 더 작은 값을 반환한다.
- 첫 번째 반복에서 a는 배열의 첫 번째 요소, b는 두 번째 요소다. 함수는 이 둘 중 더 작은 값을 반환한다.
- 이후 반복에서 a는 이전 반복의 결과값(누적된 최솟값), b는 다음 배열 요소다. 


### 최댓값
#### 링크 : https://www.acmicpc.net/problem/10818
#### 오답
```js
let fs = require('fs');

let input = fs.readFileSync('/dev/stdin').toString().split('\n').map(Number);

let maxNumber = Math.max(...input);

let answer = `${maxNumber}\n${input.findIndex((num)=>num === maxNumber + 1)}`

console.log(answer);
```
- input.findIndex((num) => num === maxNumber + 1) 부분에서 문제가 있다. 어떤 부분에서 실수했는지는 굳이 적지 않겠다... 😠
- +1을 오른쪽 소괄호 밖으로 옮겨주면 정답이 된다.

#### 다른 팁
```js
const input = require("fs")
  .readFileSync(process.platform === "linux" ? "/dev/stdin" : "./input.txt")
  .toString()
  .trim()
  .split("\n")
  .map((el) => +el); // 숫자로 변환
```

 
