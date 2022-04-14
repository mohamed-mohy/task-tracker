<template>
    <header class="container">
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
<div class="container-fluid">
    <a class="navbar-brand">{{ title }}</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
        <li class="nav-item">
        <router-link to="/" class="nav-link" active-class="active"><a>Home</a></router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link" to="/about" active-class="active">
                    <a >About</a>
    </router-link>
        </li>
    </ul>
    </div>
</div>
</nav>

    </header>
</template>
<script>
export default {
    name: 'HeaderComponent',
    props: {
        title: {
            type: String,
        }
    }
}
</script>
<style lang="scss" scoped>
.container{
    padding: 10px;
}


</style>