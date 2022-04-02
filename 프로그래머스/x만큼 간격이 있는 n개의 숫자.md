22/04/02/토

<h1>x만큼 간격이 있는 n개의 숫자</h1>

<strong>문제 설명</strong>
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

<br>

<strong>제한 조건</strong>

- x는 -10000000 이상, 10000000 이하인 정수입니다.
- n은 1000 이하인 자연수입니다.

<br>
<strong>입출력 예</strong>

| x   | n   | answer       |
| --- | --- | ------------ |
| 2   | 5   | [2,4,6,8,10] |
| 4   | 3   | [4,8,12]     |
| -4  | 2   | [-4, -8]     |

<br>

<h1>풀이</h1>
<h3>내가 푼 풀이</h3>

```javascript
function solution(x, n) {
  let answer = [];
  let i = 1;
  const addNumber = x;

  while (i <= n) {
    answer.push(x);
    x += addNumber;

    i++;
  }
  return answer;
}
```

계속 for문만 쓴 것 같아서 while문을 써보고싶어 while문으로 풀어봤다.

<br>
<h3>다른 사람 풀이</h3>

```javascript
function solution(x, n) {
  return Array(n)
    .fill(x)
    .map((v, i) => (i + 1) * v);
}
```

<br>
<h3>또 다른 사람 풀이</h3>

```javascript
function solution(x, n) {
  var answer = [];
  for (let i = 1; i <= n; i++) {
    answer.push(x * i);
  }
  return answer;
}
```

<br>
<br>

<h1>참고 </h1>

- fill
- map
