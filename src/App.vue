<template>
<header-component class="shadow" title="Task Tracker" />

<router-view v-slot="{ Component }">
    <transition name="fade" mode="out-in">
        <component :is="Component" />
    </transition>
</router-view>
<footer-component  />
  
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
/* ===== Scrollbar CSS ===== */
  /* Firefox */
  * {
    scrollbar-width: auto;
    scrollbar-color: #6c757d transparent;
  }

  /* Chrome, Edge, and Safari */
  *::-webkit-scrollbar {
    width: 12px;
  }

  *::-webkit-scrollbar-track {
    background: transparent;
  }

  *::-webkit-scrollbar-thumb {
    background-color: #6c757d;
    border-radius: 9px;
    border: 3px none #6c757d;
  }

</style>
<script>
import FooterComponent from './components/Footer-Component.vue'
import HeaderComponent from './components/Header-Component.vue'

export default {
  components: { HeaderComponent, FooterComponent },
  name: 'app',
  
}
</script>
<style lang="scss" scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity .4s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>