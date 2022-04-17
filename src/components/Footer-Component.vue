<template>
    <div class="container d-flex flex-column align-items-center text-secondary">
        <div class="col-lg-2 col-md-4 col-4 d-flex justify-content-around">
            <a href="https://github.com/mohamed-mohy"><i class="bi bi-github fs-3 text-secondary "></i></a>
            <a href="https://www.linkedin.com/in/mohamed-mohy-046a23140/"><i class="bi bi-linkedin fs-3 text-secondary"></i></a>
            <a href="mailto:m.mohy1995@gmail.com"><i class="bi bi-envelope fs-3 text-secondary"></i></a>
        </div>
        <p>
            Task-Tracker© 2022 <a href="mailto:m.mohy1995@gmail.com" class="text-secondary">Mohamed Mohy</a>. All rights reserved.
        </p>
    </div>
</template>

<script>
export default {
    name:'FooterComponent',

}
</script>

<style scoped lang="scss">
.container{
    padding: 10px;
a{
    transition: all .5s ease-in-out;
    text-decoration: none !important;
    &:hover{
        color: #eee !important;

    }
}
}
.bi{
    transition: all .5s ease-in-out;
    &:hover{
        color: #eee !important;
    }
}
</style>