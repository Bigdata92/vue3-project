<template lang="">
    <div class="card mt-2" v-for="(todo, index) in todos" :key="todo.id">  <!-- for문 "object in arr" :key=objec.key  -->
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">  <!-- 글자와 버튼이 양끝으로 배열되게 -->
          <input type="checkbox" class="form-check-input" 
                :value="todo.completed" @change="toggleTodo(index)">   <!-- props : 부모 -> 자식 o / 자식 -> 부모 x : v-model 사용 x -->


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
    props: ['todos'],
    emits: ['toggle-todo', 'delete-todo'],  // emit시, emits: []에 등록
    setup(props, { emit }) {
        // context.emit 중복 -> context 대신 { emit } 으로 사용 
        const toggleTodo = (index) => {
          emit('toggle-todo', index); // 자식 -> 부모 index 전달
        };

        const deleteTodo = (index) => {
          emit('delete-todo', index);
        };

        return {
            toggleTodo,
            deleteTodo,

        }
    },
}
</script>
<style lang="">
    
</style>