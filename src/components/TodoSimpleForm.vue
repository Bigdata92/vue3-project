<template lang="">
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
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>