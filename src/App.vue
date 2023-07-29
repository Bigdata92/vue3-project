<template>  <!-- vue 구성요소1 template - html -->
  <div class="container"> <!-- bootstrap class : 왼쪽, 오른쪽 띄어줌-->
    <h2>To-Do List</h2>
    <form action="" class="d-flex" @submit.prevent="onSubmit"> <!-- @submit : 제출시 함수 사용 / .prevent(Modifier) : 새로고침x  -->
      <div class="flex-grow-1 mr-2"> <!-- 너비 늘어나게  -->
        <input type="text" v-model="todo" class="form-control" placeholder="Type new to-do"> <!-- 너비에 text 맞추기  -->
      </div>
      <div>
        <button class="btn btn-primary" type="submit">
          Click
        </button>
      </div>
    </form>
  </div>
  {{ todos }}
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';

export default {  
  setup() {       
    const todo = ref('');
    const todos = ref([]);

    const onSubmit = () => {
      console.log(todo.value);
      todos.value.push({  // []에 object push
        id: Date.now(),  // unique
        subject: todo.value
      });
    }


    return {      
      todo,
      todos,
      onSubmit,

    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>