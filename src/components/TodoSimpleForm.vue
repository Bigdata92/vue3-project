<template lang="">
    <form action="" @submit.prevent="onSubmit"> <!-- @submit : 제출시 함수 사용 / .prevent(Modifier) : 새로고침x  -->
      <div class="d-flex">
        <div class="flex-grow-1 mr-2"> <!-- 너비 늘어나게  -->
          <input type="text" v-model="todo" class="form-control" placeholder="Type new to-do"> <!-- 너비에 text 맞추기  -->
        </div>
        <div>
          <button class="btn btn-primary" type="submit">
            Add
          </button>
        </div>
      </div>
      <div v-show="hasError" style="color: red;">
        This field cannot be empty
      </div>
    </form>
</template>
<script>

import {ref} from 'vue';

export default {
  emits: ['add-todo'],
  setup(props, { emit }) { // 부모 component로 정보 전달시, context.emit 필요
      const todo = ref('');
      const hasError = ref(false);

      const onSubmit = () => {
          if (todo.value === '') {
              hasError.value = true;
          } else { // todos는 부모 component에 o - 자식 component -> 부모로 해당 object 전달해야됨
              emit('add-todo', {  // 1번째 인자 : event 이름, 2번째 인자 : data
                  id: Date.now(),
                  subject: todo.value,
                  completed: false,
              });
              hasError.value = false;
              todo.value = '';  // Click 버튼 클릭 후, 이전 검색어 제거
          }
      };

      return {
          todo,
          hasError,
          onSubmit,

      };
  }
}
</script>
<style lang="">
    
</style>