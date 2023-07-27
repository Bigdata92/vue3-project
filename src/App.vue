<template>  <!-- vue 구성요소1 template - html -->
  <div class="name-style">{{ name }}</div>
  <button class="btn btn-primary" @click="click">
    Click
  </button>
</template>

<script>  // vue 구성요소2 script - js
export default {  
  setup() {       
    let name = 'test1';  // const는 값 수정 x -> let 변경

    // const hi = (name) => {
    //   return 'hello ' + name;
    // }
    const click = () => {
      name = 'test2';
      console.log(name);
    }

    return {      
      name,
      click,
    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>