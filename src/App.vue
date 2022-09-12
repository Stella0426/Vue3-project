<template> 
  <div class="container">
    <h2>To-Do List</h2>
    <form @submit.prevent="onSubmit">
      <div class="d-flex">
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
        <div>
          <button 
            class="btn btn-primary"
            @click="onSubmit"
          >
          Add
          </button>
        </div>
      </div>
      <div v-show="hasError" style="color:red">
        This field cannot be empty
      </div>
    </form>
    <div 
      v-for="todo in todos" 
      :key="todo.id"
      class="card mt-2"
    >
      <div class="card-body p-2">
        <div class="form-check">
          <input 
            class="form-check-input" 
            type="checkbox"
            v-model="todo.completed"
          >
          <label
            class="form-check-label"
            :class="{ todo: todo.completed }"
          >
          <!-- :style="todo.completed ? todoStyle : {}" style바인딩 (label안에 적어주기)-->
            {{ todo.subject }}
          </label>
        </div>
      </div>
    </div>
  </div>
</template>
<!-- v-show : 초기렌더링비용이많이듦(토글자주할때사용) // v-if : 토글비용많이듦(조건이runtime동안바뀌지않을때) -->
<script>
  import { ref } from 'vue';
  // import { reactive } from 'vue';

  export default {
    setup() {
      const todo = ref('');
      const todos = ref([]);
      const hasError = ref(false);
      const todoStyle = {
        textDecoration: 'line-through',
        color: 'gray'
      }

      const onSubmit = () => {
        // e.preventDefault();
        // console.log(todo.value)
        if (todo.value === '') {
          hasError.value = true
        } 
        else {
          todos.value.push({
          id: Date.now(),
          subject: todo.value,
          completed: false,
          });
          hasError.value = false;
          todo.value='';
        }
      }

      // const updateName = (e) => {
      //   console.log(e.target.value)
      //   name.value = e.target.value;
      // }


      return{
        todo,
        onSubmit,
        todos,
        hasError,
        todoStyle
        // updateName
      };
    }
  }
</script>

<style>
  .todo {
    color: gray;
    text-decoration: line-through;
  }
</style>