<template>  <!-- vue 구성요소1 template - html -->
  <div class="name-style">{{ name }}</div> <!-- script 요소 사용시 {{ 변수명 }} -->
</template>

<script>  // vue 구성요소2 script - js
export default {  // 1. export default {} 선언
  setup() {       // 2. setup() 선언
    const name = 'test1'; // 3. 변수 선언 및 할당
    return {      // 4. 변수 return
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