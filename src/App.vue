<template>  <!-- vue 구성요소1 template - html -->
  <div class="container"> <!-- bootstrap class : 왼쪽, 오른쪽 띄어줌-->
    <h2>To-Do List</h2>
    <TodoSimpleForm/>
    <div v-if="!todos.length">  <!-- todos 원소 개수가 0일때, 보여줌 -->
      추가된 todo가 없습니다.
    </div>
    <div class="card mt-2" v-for="(todo, index) in todos" :key="todo.id">  <!-- for문 "object in arr" :key=objec.key  -->
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">  <!-- 글자와 버튼이 양끝으로 배열되게 -->
          <input type="checkbox" class="form-check-input" v-model="todo.completed">
          <label class="form-check-label" 
            :class="{ todo: todo.completed }">  <!-- style .todo는 todo.completed 가 true 일때만 -->
            {{ todo.subject }}  <!-- completed : true 일때만, style 적용되게 -->
          </label>
        </div>
        <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';
import TodoSimpleForm from '@/components/TodoSimpleForm.vue'

export default {  
  components: {
    TodoSimpleForm,
  },
  setup() {       
    const todo = ref('');
    const todos = ref([]);
    const hasError = ref(false);


    const todoStyle = {
      textDecoration: 'line-through', // text-decoration -> textDecoration 사용
      color: 'gray',
    }

    const onSubmit = () => {
      if (todo.value === '') {
        hasError.value = true;
      } else {
        console.log(todo.value);
        todos.value.push({  // []에 object push
          id: Date.now(),  // unique
          subject: todo.value,
          completed: false,   // default : false
        });
        hasError.value = false;
        todo.value = '';  // Click 버튼 클릭 후, 이전 검색어 제거
      }
    }

    const deleteTodo = (index) => { // todo 삭제
      todos.value.splice(index, 1);  // array 에서 index 일치하는 놈, 1개만 제거
    };

    return {      
      todo,
      todos,
      onSubmit,
      hasError,
      todoStyle,
      deleteTodo, 

    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.todo {
  color: gray;
  text-decoration: line-through;
}
</style>