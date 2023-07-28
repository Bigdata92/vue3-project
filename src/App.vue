<template>  <!-- vue 구성요소1 template - html -->
  <div class="name-style">{{ name }}</div>
  <input :type="type" :value="name" :class="name"> <!-- 변수 name을 input value에 binding -->
  <button class="btn btn-primary" @click="click">
    Click
  </button>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';

export default {  
  setup() {       
    const name = ref('test1');  // ref: 기본 자료형, Object, Array
    const type = ref('number'); // input type 변수 가능
    const nameClass = ref('');  // class로 변수 가능

    const click = () => {
      name.value = 'test2'; // ref는 data 접근시 .value 붙여야함
      type.value = 'text';
      nameClass.value = 'name';
    }

    return {      
      name,
      click,
      type,
    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>