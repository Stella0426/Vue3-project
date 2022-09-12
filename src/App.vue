<!-- component : 하나의 부품을 의미함 따라서 여러곳에서 가져다 쓰일 수 있음 -->
<!-- 뷰 컴포넌트 : 세개의 부분으로 나누어짐 
  1. template(템플릿 안에는 html 코드가 들어감)
  2. script(스크립트 안에는 js 로직이 들어감)
  3. style(css 코드가 들어감)
-->
<template>
  <div class="name">{{ name }}</div>
  <div>Hi</div>
  <!-- vue.js 2 : 하나의 큰 div로 묶어줘야했었다.(아래 예시 참고)
    <div>
      <div class="name">{{ name }}</div>
      <div>Hi</div>
    </div> 
  하지만 ver.3부턴 안그래도 됨 -->
</template>

<script>
  export default {
    setup() {
      const name = 'Kossie Coder1';

      return{
        name
        // 변수를 리턴해주면 이 안의 변수들은 template안에서 접근이 가능해짐
        // template 안에서 접근해주려면 {{데이터의 변수}} 콧수염문법 써주기
      };
    }
  }
</script>

<style>
  .name{
    color: red;
  }
</style>