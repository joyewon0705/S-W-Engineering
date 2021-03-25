# GFM Extended Syntax Guide

## Tables

- 헤더 행, 헤더와 데이터를 구분하는 행, 데이터 행으로 구성된 행과 열의 데이터 배열임.
- 올바르게 렌더링하려면 테이블 앞에 빈 줄을 포함해야 함.
- 헤더 행과 구분자 행의 칸 수가 같아야 함.
- 구분자 행에는 최소 세 개의 하이픈(-)을 입력해야 함.
  
  입력:
      
      | First Header  | Second Header |
      | ------------- | ------------- |
      | Content Cell  | Content Cell  |
      | Content Cell  | Content Cell  |
    
  출력:
      
    | First Header  | Second Header |
    | ------------- | ------------- |
    | Content Cell  | Content Cell  |
    | Content Cell  | Content Cell  |
    
- 테이블 양 끝에 있는 파이프(|)는 선택사항임.
- 파이프(|)를 텍스트로서 출력하려면 파이프 앞에 \ 문자를 추가함.
- 테이블 내에 링크, 코드, 텍스트 서식 등을 적용할 수 있음.

  입력:

      | Command | Description |
      | --- | --- |
      | `git status` | List all *new or modified* files |
      | `git diff` | Show file differences that **haven't been** staged |
      
  출력:
  
  | Command | Description |
  | --- | --- |
  | `git status` | List all *new or modified* files |
  | `git diff` | Show file differences that **haven't been** staged |
  
- 구분자 행에 콜론을 추가해 텍스트를 왼쪽, 가운데, 오른쪽으로 정렬함.

  입력:
  
      | Left-aligned | Center-aligned | Right-aligned |
      | :---         |     :---:      |          ---: |
      | git status   | git status     | git status    |
      | git diff     | git diff       | git diff      |
      
  출력:
  
  | Left-aligned | Center-aligned | Right-aligned |
  | :---         |     :---:      |          ---: |
  | git status   | git status     | git status    |
  | git diff     | git diff       | git diff      |
  
- 데이터 행의 칸 수가 헤더 행의 칸 수보다 적을 경우 빈 칸이 추가되고 많을 경우 초과된 칸은 무시됨.

  입력:
  
      | abc | def |
      | --- | --- |
      | bar |
      | bar | baz | boo |
      
  출력:
  
  | abc | def |
  | --- | --- |
  | bar |
  | bar | baz | boo |
  
## Task lists

- **[ ] 항목** 형식의 체크 박스가 있는 목록 리스트임.
- 항목을 체크하고 싶다면 괄호 사이에 X 또는 x를 입력함.
  
  입력:
  
      - [x] Finish my changes
      - [ ] Push my commits to GitHub
      - [ ] Open a pull request
  
  출력:
  
  - [x] Finish my changes
  - [ ] Push my commits to GitHub
  - [ ] Open a pull request

- 항목이 괄호로 시작하는 경우 \ 문자로 이스케이프해야 함.

  입력:
  
      - [ ] \(Optional) Open a followup issue
  
  출력:
  
  - [ ] \(Optional) Open a followup issue

- 작업 목록은 중첩될 수 있음.
- 최종적으로 렌더링 된 문서에서 체크 여부를 동적으로 처리할 수 있음.

## Strikethrough

- 취소선을 표시하려면 텍스트 앞뒤에 ~ 문자 두 개를 추가함.
  - 예) \~\~this\~\~ -> ~~this~~

## Autolinks

- GitHub에서 표준 URL은 자동으로 링크로 변환됨.
  - 예) Visit https://github.com
- `www.` 뒤에 유효한 도메인 주소가 있어야 함.
- 유효한 도메인은 마침표(.)로 나눠진 밑줄(\_) 및 하이픈(-), 영숫자 세그먼트로 구성됨.
- 마침표가 하나 이상 있어야 하며 도메인의 마지막 두 세그먼트에 밑줄이 없어야 함. 
- scheme `http`는 자동으로 적용됨.
- 도메인 뒤에는 공백 또는 < 문자를 제외한 문자가 올 수 있음.
- < 문자는 자동링크를 즉시 끝냄.
  - 예) www.commonmark.org/he<lp
- 맨 뒤 구두점(?, !, ., ,, \:, \*, \_, \~)은 링크에 포함되더라도 자동 링크로 간주되진 않음.
  - 예) www.commonmark.org.
- 자동링크가 ) 문자로 끝날 경우, 총 괄호 수를 비교해 일치하지 않는 괄호는 고려하지 않음.
  - 예) www.google.com/search?q=Markup+(business)))
- 자동링크가 ; 문자로 끝날 경우, entity reference(`&`+하나 이상의 영숫자+`;`)인지 확인하고 맞으면 링크에서 제외함.
  - 예) www.google.com/search?q=commonmark&hl;

### email autolink

- 이메일 주소는 다음 규칙에 따라 인식됨
  - 하나 이상의 영숫자 또는 ., \-, \_, + 문자
  - `@` 기호
  - 마침표(.)로 나눠진 하나 이상의 영숫자 또는 \-, \_ 문자
  - 적어도 하나의 마침표가 있어야 하며 마지막 문자로 \- 와 \_ 문자는 올 수 없음.
- scheme `mailto:`는 자동으로 적용됨.
- \+ 문자는 @ 앞에만 올 수 있음.
  - 예) hello@mail+xyz.example    hello+xyz@mail.example
- ., \-, \_ 문자는 @ 앞뒤로 모두 올 수 있지만 마침표(.)만 이메일 주소 끝에 올 수 있음.
  - 예) a.b-c_d@a.b    a.b-c_d@a.b.    a.b-c_d@a.b-    a.b-c_d@a.b_
