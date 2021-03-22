# S-W-Engineering
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
