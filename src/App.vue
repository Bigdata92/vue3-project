<template>  <!-- vue 구성요소1 template - html -->
  <div class="name-style">{{ hi('codemonkey') }}</div>
  <div>{{ greeting }}</div>
</template>

<script>  // vue 구성요소2 script - js
export default {  
  setup() {       
    const name = 'test1'; 

    const hi = (name) => {
      return 'hello ' + name;
    }

    const greeting = hi(name);

    return {      
      hi,
      greeting,
    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.name-style {
  color: red;
}
</style>