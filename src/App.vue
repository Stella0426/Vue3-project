<template> 
  <div class="container">
    <h2>To-Do List</h2>
    <form
      @submit.prevent="onSubmit" 
      class="d-flex"
    >
      <div class="flex-grow-1 mr-2">
        <input 
          class="form-control"
          type="text" 
          v-model="todo"
          placeholder="Type new to-do"
        >
      <!-- @input="updateName" -->
      <!-- :value="name" -->
      <!-- 위 두개를 input안에 써주지않고 v-model(value 바인딩도 해주고,name값이 변경되었을때 값도 알아서 업뎃해주는게 한방에 가능) 
        한번만 적어주면 끝!-->
      </div>
      <div class="">
        <button 
          class="btn btn-primary"
          @click="onSubmit"
        >
        Add
        </button>
      </div>
    </form>
    <div class="card mt-2">
      <div class="card-body p-2">
        {{todos[0].subject}}
      </div>
    </div>
  </div>
</template>

<script>
  import { ref } from 'vue';
  // import { reactive } from 'vue';

  export default {
    setup() {
      const todo = ref('');
      const todos = ref([
        {id:1, subject:'흠이 생일선물 사기'},
        {id:2, subject:'흠이 빼빼로 만들어주기'}
      ]);

      const onSubmit = () => {
        // e.preventDefault();
        // console.log(todo.value)
        todos.value.push({
          id: Date.now(),
          subject: todo.value
        });
      }

      // const updateName = (e) => {
      //   console.log(e.target.value)
      //   name.value = e.target.value;
      // }

      return{
        todo,
        onSubmit,
        todos
        // updateName
      };
    }
  }
</script>

<style>
</style>