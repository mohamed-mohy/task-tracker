<template>
<header-component title="Task Tracker" />
<Transition>
  <router-view/>
</Transition>
  
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
<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
    transition: all .8s ease-in-out;
}
.v-enter-from,
.v-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>