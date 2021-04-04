<template>
  <img alt="Vue logo" src="./assets/logo.png" class="img">
  <HelloWorld msg="Hello Vue.js !"/>
  <Test :="text"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Test from './components/Test.vue';

export default {
  name: 'App',

  data:() => ({
     text:{
       text1:"Click Me !",
       text2:"Click !"
     }
  }),
  components: {
    HelloWorld,
    Test
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.img{
  animation: spin 1.3s infinite linear;
}
@keyframes spin{
  0%{
    transform: rotate(0deg);
  }
  100%{
    transform: rotate(360deg);
  }
}
</style>
