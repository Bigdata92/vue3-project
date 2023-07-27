<template>  <!-- vue 구성요소1 template - html -->
  <div class="name-style">{{ name }}</div>
  <div>Hi</div>
</template>

<script>  // vue 구성요소2 script - js
export default {  
  setup() {       
    const name = 'test1'; 
    return {      
      name,
    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>