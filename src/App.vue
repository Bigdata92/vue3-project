<template>  <!-- vue 구성요소1 template - html -->
  <input type="text" :value="name"> <!-- 단방향, 화면(template) 에서 값 변경시, 변수(script) 에서 값 변경 x -->
  <input type="text" v-model="age"> <!-- 양방향, 화면(template) 에서 값 변경시, 변수(script) 에서 값 변경 o -->
  <button class="btn btn-primary" @click="onSubmit">
    Click
  </button>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';

export default {  
  setup() {       
    const name = ref('test1');
    const age = ref(10);

    const onSubmit = () => {
      console.log(name.value);
      console.log(age.value);
    }


    return {      
      name,
      onSubmit,
      age,

    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>