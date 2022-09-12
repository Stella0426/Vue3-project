<!-- component : 하나의 부품을 의미함 따라서 여러곳에서 가져다 쓰일 수 있음 -->
<!-- 뷰 컴포넌트 : 세개의 부분으로 나누어짐 
  1. template(템플릿 안에는 html 코드가 들어감)
  2. script(스크립트 안에는 js 로직이 들어감)
  3. style(css 코드가 들어감)
-->
<template> 
  <!-- v-bind === : , v-on: === @ -->
  <div v-bind:class="nameClass">{{ name }}</div>
  <!-- 템플릿안에서는 name.value를 쓰지않아도 name만 써도 화면에 출력되게 만듦 -->
  <input :type="type" :value="name">
  <!-- 바인딩 : 연결하다 -->
  <div>Hi</div>
  <button 
    class="btn btn-primary"
    @click="updateName"
  >Click</button>
  <!-- <div>{{ greeting(name) }}</div> -->
  <!-- 
    vue.js 2 : 하나의 큰 div로 묶어줘야했었다.(아래 예시 참고)
    <div>
      <div class="name">{{ name }}</div>
      <div>Hi</div>
    </div> 
  하지만 ver.3부턴 안그래도 됨 
  -->
</template>

<script>
  import { ref } from 'vue';
  // import { reactive } from 'vue';

  export default {
    setup() {
      const name = ref('Heum');
      //data값이 변경되면 template의 값도 변경되는데 이걸 reactive하다고 표현함
      //ref()안에는 숫자, object{}, 배열[] 등이 들어가도 모두 가능해!!
      // const name = reactive({id:1}) or const name = reactive([]) 
      
      // const greeting = (name) => {
      //   return 'Hello, ' + name;
      // }

      const type = ref('number');
      const nameClass = ref('');
      // const nameClass = ref('') -> 클래스명이 사라진거라서 빨간글씨가 아닌 검정글씨로 화면에 찍힘
      // 아래 함수에 nameClass.value = 'name';를 적어주면 ref('')비어두면 버튼클릭하면 빨간글씨로 찍힘

      const updateName = () => {
        name.value = 'Byul'; //값을 변경할땐 .value 써야함! 객체 : name.value.id이렇게! => 객체와 배열은 name.id = 2; 이런식으로 value안쓰고 사용가능
        console.log(name)
        // name이란 변수 값이 변경되어도 template에서 쓰이는 값은 변경되지 X!!
        // 그래서 vue.js에서는 기능을 제공함 -> ref!!!
        // 일반 변수를 사용해서 값을 담아주면 안되고 ref를 사용해서 담아줘야 변경됨.
        type.value = 'text';
        nameClass.value = 'name';
      }

      return{
        name,
        updateName,
        type,
        nameClass
        // greeting,
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