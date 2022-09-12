<template> 
  <input 
    type="text" 
    v-model="name"
  >
  <!-- @input="updateName" -->
  <!-- :value="name" -->
  <!-- 위 두개를 input안에 써주지않고 v-model(value 바인딩도 해주고,name값이 변경되었을때 값도 알아서 업뎃해주는게 한방에 가능) 
    한번만 적어주면 끝!-->
  <button 
    class="btn btn-primary"
    @click="onSubmit"
  >Click
  </button>
</template>

<script>
  import { ref } from 'vue';
  // import { reactive } from 'vue';

  export default {
    setup() {
      const name = ref('Heum');

      const onSubmit = () => {
        console.log(name.value)
      }

      // const updateName = (e) => {
      //   console.log(e.target.value)
      //   name.value = e.target.value;
      // }

      return{
        name,
        onSubmit,
        // updateName
      };
    }
  }
</script>

<style>
  .name{
    color: red;
  }
</style>