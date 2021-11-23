<template>
  <Header title="Store Resources Change"/>
  <Resources/>
</template>

<script>
import Header from './components/Header.vue'
import Resources from './components/Resources/Resources.vue'
export default {
  name: 'App',
  components: {
    Header,
    Resources
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
button {
    padding: 0.75rem 1.5rem;
    font-family: inherit;
    background-color: #3a0061;
    border: 1px solid #3a0061;
    color: #fff;
    cursor: pointer;
}
button:hover {
    background-color: #270041;
    border-color: #270041;
}
.flat {
    background-color: transparent;
    color: #3a0061;
    border: none;
}
.flat:hover {
    background-color: #edd2ff;
}
</style>
