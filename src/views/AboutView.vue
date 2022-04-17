<template>
<div>

    <div v-show="isLoading">
        <spinner-component/>
    </div>
    <div class="about d-flex justify-content-center align-content-center align-items-center flex-column " v-show="!isLoading">
    <div v-show="!isLoading" class="pt-5 text-white text-center">
        <h2>About</h2>
        <p>This is the about page</p>
       
    </div>
    </div>
</div>
</template>
<script>
import SpinnerComponent from '@/components/Spinner-Component.vue'
export default {
    name: 'AboutView',
    components: {
        SpinnerComponent
    }
    ,data() {
        return {
            isLoading: true,
        }
        },
    mounted() {
        setTimeout(() => {
            this.isLoading = false;
        }, 500);
    },
    
}
</script>
<style lang="scss" scoped>
.container{
    padding: 10px;
}
.about{
    min-height: calc(100vh - 200px);
}
</style>