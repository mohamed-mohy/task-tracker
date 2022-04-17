<template>
  <div class="home h-100">
    <body-component/>
  </div>
</template>

<script>
// @ is an alias t  o /src
import BodyComponent from '@/components/Body-Component';


export default {
  name: 'HomeView',
  components: {
    BodyComponent,
  },
  
}
</script>
<style lang="scss" scoped>
.home{
    min-height: calc(100vh - 200px);
}
</style>