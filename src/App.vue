<template>
  <Nav />

  <img class="astro" src="../public/astr.png" alt="">

  <Form />
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Nav from './components/Nav.vue'
import Form from './components/Form.vue'


export default {
  name: 'App',
  components: {
    Nav,
    Form
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
  margin: 0px;
}

body {
  padding: 0;
  margin: 0;
  /* background-image: url("../public/space.jfif"); */
  background-color: #000000;
  color: white;
}

.astro {
  margin-top: 5%; /* Adjust the margin as needed for spacing */
  position: absolute;
  top: 8%; /* Initial position above the container */
  left: 50%; /* Center horizontally */
  transform: translateX(-50%);
  animation: slideIn 2s ease-in-out;
}

@keyframes slideIn {
  0% {
    top: -10%; /* Move 10% above the final position */
  }
  100% {
    top: 10%; /* Move 10% above the final position */
  }
}


</style>
