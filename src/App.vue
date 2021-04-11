<template>
  <div id="app">
    <h1>Send Email Implement</h1>
    <SendEmailForm />
  </div>
</template>

<script>
import SendEmailForm from "./components/SendEmailForm.vue";

export default {
  name: "App",
  components: {
    SendEmailForm
  }
};
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
</style>
