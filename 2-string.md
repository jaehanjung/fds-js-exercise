### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```
```js
function insensitiveEqual(str1,str2){
  return  str1.toLowerCase() === str2.toLowerCase()
}
```
### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```
```js
function leftpad(s,n){
  if(s.length < n){
    const spaceLength = n - s.length;
   return ' '.repeat(spaceLength) + s
  } else{
    return s
  }
}

// 과제 for 루프써서 해보기
```
### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js
function countVowel(str){
  let count = 0;
  for (let i = 0 ; i< str.length; i++){
    if(
      str[i] === 'a'||
      str[i] === 'e'||
      str[i] === 'i'||
      str[i] === 'o'||
      str[i] === 'u'
      ) {
      count++;
    } 
  }
  return count;
}
```
### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```
```js
function countChar(str){
  let obj = {};
  for (let i = 0; i< str.length;i++){
     const char = str[i];
     // 만약 속성이 없다면 속성값에 1저장
    //  대괄호 표기법을 쓰는 이유는 객체의 제목이 문자열이기때문이다.
     if(obj[char] == undefined){
       //속성 값에 1저장
       obj[char] = 1;
     }else{
       // 속성이 있으면 증가
       obj[char]++;
     }
  }return obj
}
```
```js
function count(str){
  let obj = {};
  for(let i=0; i< str.length;i++){
    if(obj[str[i]] === undefined){
      obj[str[i]] = 1;
    }else{
      obj[str[i]]++
    }
  }
  return obj
}
```
### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)
```js
function isPalindrome(str){
  for (let i =0; i< str.length;i++){
    if(str[i] !== str[str.length - i - 1]){
      return false
    }
  }
  return true;
}
```
### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```
```js
function subString(str){
  let arr =[];
  for (let i = 0; i< str.length;i++){
    for(let j = i+1; j< str.length+1; j++){
      console.log(i,j);
      arr.push(str.slice(i, j))
    }
  }
  return arr;
}
// i가 0일때는 j가 1이여야한다.

// str햄버거가 들어오면
// i에 0이들어간채로 포문이돈다
// 2번쨰 포문에 1이들어간채로 3까지 돈다.
// 바깥으로 튀어나오면 다시 바깥 처음으로 돌아가서 i가 1인상태로 안쪽코드가 다시실행된다.
// 두번쨰 포문 j가 2가되서 시작된다.그러면 2부터 3까지 돈다
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```
```js
function removeDuplicates(str){
  let newstr = '';
  for(let i =0; i< str.length; i++){
    if(newstr.includes(str[i])){
    
   } else{
     newstr += str[i];
   }
 }
 return newstr;
}

// 만약 내가지금 쓰고잇는곳에 내가 str을 적은적이없다면
// newstr 에 추가시켜줘라.
```
### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.
```js
function secureEmail(email){
   const arr = email.split('@');
  const stars = '*'.repeat(arr[0].length);
  const domain = arr[1];
  return stars +'@'+ domain
}
 
```
### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.
```js
function swapCase(str){
  let newStr = '';
  for(let i=0;i<str.length;i++){
    if(str[i].toLowerCase() === str[i]){
      newStr += str[i].toUpperCase();
    }else{
      newStr += str[i].toLowerCase();
    }
  }
  return newStr;
}
```
### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
```js
function capitalize(str){
 let newstr = '';
 for(let i= 0; i<str.length;i++){
   if(i === 0 || str[i - 1] === ' ' ){
     newstr += str[i].toUpperCase();
   }else{
     newstr += str[i];
   }
 }
 return newstr
}
```

### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
```js
function maxlength(str){
  let currentlen = 0;
  let maxlen = 0;
  for (let i=0;i <str.length; i++){
    if(str[i] === ' '){
      maxlen = maxlen > currentlen ? maxlen : currentlen;
      currentlen = 0;
    } else{
      currentlen++;
    }  
  }
  return maxlen > currentlen ? maxlen : currentlen;
}
```
```js
//split메소드사용
function maxlength(str){
  const arr = str.split(' ');
  console.log(arr)
  let maxlen = 0;
  for (let i=0; i< arr.length; i++){
    console.log(arr[i].length)
    maxlen = arr[i].length > maxlen ? arr[i].length : maxlen;
  }
  return maxlen;
}
```

### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.
```js
function firstStr(s,n){
  let newStr = '';
  for(let i= 0; i<n;i++ ){
    newStr += s[i];
  }
  return newStr;
}
```
과제
### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.
```js
function camelToSnake(str){
  let newStr = '';
  for(let i =0; i<str.length;i++){
    if(str[i] === str[i].toUpperCase() && i !== 0){
      newStr += `_${str[i].toLowerCase()}`;
    } else {
      newStr +=str[i]
    }
  }
  return newStr;
}
```
과제
### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.
```js
function arr(str) {
  let newStr = '';
  for (let i = 0; i < str.length; i++) {
    if (str[i - 1] === `_` || str[i] === str[0]) {
      newStr += str[i].toUpperCase();
    } else if (str[i] !== '_') {
      newStr += str[i];
    }
  }
  return newStr;
}

```
과제
### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```
```js
function split(str, n){
  let newStr = '';
  let newArr = [];
  for(let i = 0; i< str.length;i++){
    if(str[i] !== n){
    newStr += str[i];
    // console.log(newStr)
    } else{
       newArr.push(newStr);
      newStr ='';
      // console.log(newArr)
    }
  }
    newArr.push(newStr)
      return newArr;
  
}
```
과제

### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```
```js
function convertBinary(str){
 const arr = [...str];
 console.log(arr)
 arr.reverse();
 console.log(arr)
 let num = 0;
 
 for(let i=0; i<arr.length;i++){
   if(arr[i] === '0'){
     num += 0;
   }
   else{
     num += 2**i;
   }
 }
 return num;
}
```
과제

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
