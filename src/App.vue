<template>
<header-component title="Task Tracker" />
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
body
{
  background-color:#212529 !important;
}

</style>
<script>
import HeaderComponent from './components/Header-Component.vue'

export default {
  components: { HeaderComponent },
  name: 'app',
  
}
</script>