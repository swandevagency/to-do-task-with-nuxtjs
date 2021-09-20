<template>

<div class="div">
  <navbar />
  <h1>Welcome to Mehraeen's task manager</h1>
</div>
</template>

<script>
import navbar from '../components/navbar.vue'
export default {
  components:{
    navbar
  }
}
</script>
<style>
  body{
    margin: 0;
  }
  div{
    width: 100vw;
    text-align: center;

  }
  h1{
    position: relative;
    top: 20px;
    font-size: 40px;
    color:black;
  }
</style>
