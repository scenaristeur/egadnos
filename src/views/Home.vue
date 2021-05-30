<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <b-container class="form-container">
      <Form />
    </b-container>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Form from '@/components/Form.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Form
  }
}
</script>
<style>
.form-container{
  text-align: left;
}
</style>
