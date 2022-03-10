22/03/10/목

<h1>K번째수</h1>

<strong>문제 설명</strong>  
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

<br>

<strong>제한사항</strong>

- array의 길이는 1 이상 100 이하입니다.
- array의 각 원소는 1 이상 100 이하입니다.
- commands의 길이는 1 이상 50 이하입니다.
- commands의 각 원소는 길이가 3입니다.

<br>
<strong>입출력 예</strong>

| array                 | commands                          | return    |
| --------------------- | --------------------------------- | --------- |
| [1, 5, 2, 6, 3, 7, 4] | [[2, 5, 3], [4, 4, 1], [1, 7, 3]] | [5, 6, 3] |

<br>

<h1>풀이</h1>
<h3>내가 푼 풀이</h3>

```javascript
function solution(array, commands) {
  let answer = [];
  for (let index = 0; index < commands.length; index++) {
    const i = commands[index][0] - 1;
    const j = commands[index][1];
    const k = commands[index][2] - 1;

    const arr = array.slice(i, j).sort((a, b) => a - b);
    const element = arr[k];
    answer.push(element);
  }

  return answer;
}
```

: `const arr = array.slice(i, j).sort()` 라고 쓰고 제출했을 때는 한 문제에서 오류가 났다.

: `const arr = array.slice(i, j).sort((a, b) => a - b);` 정확하게 어떻게 sort를 할건지 코드에서도 명확하게 써주도록 하자.

<br>
<br>
<h3>다른 사람 풀이</h3>

```javascript
function solution(array, commands) {
  return commands.map((command) => {
    const [sPosition, ePosition, position] = command;
    const newArray = array
      .filter(
        (value, fIndex) => fIndex >= sPosition - 1 && fIndex <= ePosition - 1
      )
      .sort((a, b) => a - b);

    return newArray[position - 1];
  });
}
```

: map 메서드와 filter, 구조분해할당을 사용해서 푼 코드.

<br>
<br>
<h3>또 다른 풀이</h3>

```javascript
function solution(array, commands) {
  let answer = [];
  for (let i = 0; i < commands.length; i++) {
    let eachCommand = commands[i];
    let slice = array.slice(eachCommand[0] - 1, eachCommand[1]);
    answer.push(slice.sort((a, b) => a - b)[eachCommand[2] - 1]);
  }

  return answer;
}
```
