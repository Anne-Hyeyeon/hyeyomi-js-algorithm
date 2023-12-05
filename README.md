# hyeyomi-js-algorithm

- [패스트캠퍼스 프론트엔드 초격차 패키지](https://fastcampus.co.kr/dev_online_fesignature) 中 Course 3, JavasScript로 끝내는 자류구조/알고리즘 강의를 듣고 작성하는 강의 노트입니다. 
- 대표 알고리즘의 기본형을 정리할 예정입니다.

## Intro
- 빈도가 높은 알고리즘 유형에는 '구현', 'DFS/BFS(탐색)', '탐욕' 알고리즘 유형이 출제 빈도가 높은 편이다.
- 코딩테스트 대비 : 알고리즘 유형 별로 이론 및 핵심 문제를 10개 이상 풀어보기. (수학 공부와 크게 다르지 않은 걸?)
- 알고리즘 문제 난이도는, 컴퓨터공학 학부 과정에서 배우는 기초 내용 정도이다. 
- 원하는 기업의 기출 문제를 푸는 것도 중요하다.

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

### 기본 출력
- 일반적인 알고리즘을 풀 때, 표준 출력으로 console.log()를 이용한다.
```js
// 단순히 문자열을 출력한다.
console.log('Hello World!');

result = 35;
// 템플릿 리터럴을 사용해 문자열 내부에 변수를 포함.
console.log(`정답은 ${result}입니다.`);
```

#### Javscript 기본 사칙 연산 관련 Tip
- parseInt(a/b)를 할 경우, 몫만 남는다.

### JS 빠른 출력
- JS로 코딩 테스트 문제를 풀 때, 출력 과정만으로 시간 초과를 받을 때가 있다.
- 출력 시간을 다눛갛기 위해 다음과 같은 방법을 유용하게 사용할 수 있다. -> 한꺼번에 뭉쳤다가 출력
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

### 기본 입력 - fs 모듈
- 입력 데이터가 텍스트 파일 형태로 주어지는 경우, 파일 시스템 모듈을 사용함.
- 예시) 전체 텍스트를 읽어온 뒤, 줄바꿈 기호를 기준으로 구분하여 리스트로 변환.
```js
//readline 모듏보다는 fs를 이용하는 게 좋다.
let fs = require('fs');
let input = fs.readFileSync('dev/stdin').toString().split('\n');
// let input = fs.readFileSync('input.txt').toString().split('\n');

console.log(input);
