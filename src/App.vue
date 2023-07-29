<template>  <!-- vue 구성요소1 template - html -->
  <div v-if="toggle">true</div> <!-- v-show : style을 이용해서 보여줌 / toggle 자주 할때 -->
  <div v-else>false</div>       <!-- v-if : 조건 만족 o 만 랜더링 / 조건이 거의 바뀌지 x -->
  <button @click="onToggle">toggle btn</button>
  <div class="container"> <!-- bootstrap class : 왼쪽, 오른쪽 띄어줌-->
    <h2>To-Do List</h2>
    <form action="" @submit.prevent="onSubmit"> <!-- @submit : 제출시 함수 사용 / .prevent(Modifier) : 새로고침x  -->
      <div class="d-flex">
        <div class="flex-grow-1 mr-2"> <!-- 너비 늘어나게  -->
          <input type="text" v-model="todo" class="form-control" placeholder="Type new to-do"> <!-- 너비에 text 맞추기  -->
        </div>
        <div>
          <button class="btn btn-primary" type="submit">
            Click
          </button>
        </div>
      </div>
      <div v-show="hasError" style="color: red;">
        This field cannot be empty
      </div>
    </form>
    <div class="card mt-2" v-for="todo in todos" :key="todo.id">  <!-- for문 "object in arr" :key=objec.key  -->
      <div class="card-body p-2">
        {{ todo.subject }}
      </div>
    </div>
  </div>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';

export default {  
  setup() {       
    const toggle = ref(false);
    const onToggle = () => {
      toggle.value = !toggle.value
    };
    const todo = ref('');
    const todos = ref([
      {id: 1, subject: '휴대폰 사기'},
      {id: 2, subject: '장보기'},
    ]);
    const hasError = ref(false);

    const onSubmit = () => {
      if (todo.value === '') {
        hasError.value = true;
      } else {
        console.log(todo.value);
        todos.value.push({  // []에 object push
          id: Date.now(),  // unique
          subject: todo.value
        });
        hasError.value = false;
      }
    }


    return {      
      todo,
      todos,
      onSubmit,
      toggle,
      onToggle,
      hasError,

    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>