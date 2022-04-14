<template>
  <div class="home">
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
