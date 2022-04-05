<template>
  <SignupForm />
</template>

<script>
import SignupForm from './components/SignupForm.vue'

export default {
  components: {
    SignupForm,
  },
}
</script>

<style lang="scss">
#app {
  color: #2c3e50;
  font-family: 'Bitter', serif;
  margin-top: 60px;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  background-color: #eee;
  box-sizing: border-box;
  margin: 0;
}
</style>
