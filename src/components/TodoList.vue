<template lang="">
    <div class="card mt-2" v-for="(todo, index) in todos" :key="todo.id">  <!-- for문 "object in arr" :key=objec.key  -->
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">  <!-- 글자와 버튼이 양끝으로 배열되게 -->
          <input type="checkbox" class="form-check-input" v-model="todo.completed">
          <label class="form-check-label" :class="{ todo: todo.completed }">  <!-- style .todo는 todo.completed 가 true 일때만 -->
            {{ todo.subject }}  <!-- completed : true 일때만, style 적용되게 -->
          </label>
        </div>
        <button class="btn btn-danger btn-sm" @click="deleteTodo(index)">Delete</button>
      </div>
    </div>
</template>
<script>
export default {
    props: ['sendTodos'],
}
</script>
<style lang="">
    
</style>