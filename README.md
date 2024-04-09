# 열매 HTML 코딩 컨벤션

## 목차

## 1. Syntax
- 들여쓰기는 2개의 공백 문자(소프트탭)을 사용한다.
- 모든 엘리먼트 명과 애트리뷰트 명은 케밥 표기법(kebab-case)으로 작성한다.
- 모든 애트리뷰트 값은 큰 따옴표(")로 감싼다.
- 닫는 태그가 선택적이라도 생략하지 않는다. (ex: </li>, </body>)
- 주석은 `<!-- -->`으로 표기한다.
  - 수정사항 등을 기재하기 위한 주석 (주석에 년도날짜 / 수정내용 표기는 반드시 해야 한다)
```
<!-- start: 20240405 수정 및 추가 -->
<div> ... 수정 내역 ... </div>
<!-- end: 20240405 수정 및 추가 -->
```
    

## 2. Doctype
- HTML5 Doctype을 사용한다.
```
<!DOCTYPE html>
```
- 자기 마침 태그에 후행 슬래시(`/`)를 사용하지 않는다
```
<!-- Bad -->
<input />
<br />

<!-- Good -->
<input>
<br>
```

## 3. 엘리먼트
### 3.1. 스타일 제어가 어려운 엘리먼트
자식 엘리먼트 태그가 한정적이거나(ex. `<table>`) 스타일 제어에 한계를 가진 엘리먼트(ex. `<select>`)가 컴포넌트의 루트 역할로 쓰일 땐 나중에 발생할 유지보수를 고려해 `<div>`나 `<span>` 엘리먼트로 감싸는 것을 권장한다.

```
<!-- Not Bad -->
<table class="table"></table>
<select class="combobox"></select>

<!-- Good -->
<div class="table">
  <table></table>
</div>
<span class="combobox">
  <select></select>
</span>
```

### 3.2. 테이블 제목
`<caption>` 엘리먼트의 뷰를 숨길 때는 새로운 엘리먼트로 감싼다.
```
<!-- Bad -->
<table>
  <caption class="blind">My Caption</caption>
</table>

<!-- Good -->
<table>
  <caption>
    <div class="blind">My Caption</div>
  </caption>
</table>
```

## 4. 애프티뷰트
애트리뷰트는 변하지 않는 것부터 선언한다.

```
<input class="input" type="text" id="user-id" name="UserId" title="아이디" style="width:100px">
<input class="input" type="password" id="user-pw" name="UserPw" title="비밀번호" style="width:120px">
```

### 4.1. Boolean 애트리뷰트
HTML5에서는 Boolean 애트리뷰트를 선언하는 것 만으로도 true 값을 가진다. 필요하지 않다면 값을 작성하지 않는다.

```
<!-- Not Bad -->
<button disabled="true"></button>

<!-- Good -->
<button disabled></button>
```

### 4.2. name 애트리뷰트
name 애트리뷰트 값은 비즈니스 로직을 작성하는 언어의 네이밍 규칙에 맞게 작성하는 것을 권장한다.
```
<!-- PascalCase -->
<form class="form" id="my-form" name="MyForm">
  <input class="input" type="text" id="my-user-name" name="MyUserName">
</form>
```
