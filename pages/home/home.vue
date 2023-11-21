<template>
    <nav class="navbar navbar-expand-lg bg-primary">
        <div class="container-fluid">
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo02"
                aria-controls="navbarTogglerDemo02" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item mr-8">
                    </li>
                    <li class="nav-item">
                        <img src="~/assets/img/smk4.png" alt="" style="height: 60px;">
                    </li>
                    <li class="nav-item">
                        <img src="~/assets/img/wefraz.png" alt="" style="width: 80px; ">
                    </li>
                </ul>
                <form class="d-flex" role="search">
                    <a class="nav-link disabled" aria-disabled="true" style="margin-right: 20px;">LIBRARY SMKN 4 TASIKMALAYA</a>
                </form>
            </div>
        </div>
    </nav>
    <div class="conten " style="width: 100%; height: 5;">
        <img src="~/assets/img/PER.jpg" style="width: 100%; height: 400px;">

    </div>
    <div class="row" style="padding-top: 80px; padding-bottom: 80px;">
        <div class="col">
        </div>
        <div class="col">
            <form class="d-flex" role="search">
                <NuxtLink to="/rekomen" class="btn btn-dak"><button type="button" class="btn btn-primary btn-lg">RECOMMENDED</button></NuxtLink>
            </form>
        </div>
        <div class="col">
            <form class="d-flex" role="search">
                <NuxtLink to="/" class="btn btn-dak"><button type="button" class="btn btn-primary btn-lg">BOOK  SEARCH ?</button></NuxtLink>
                
            </form>
        </div>
        <div class="col">
            <form class="d-flex" role="search">
                <NuxtLink to="/about" class="btn btn-dak"><button type="button" class="btn btn-primary btn-lg">ABOUT THE LIBRARY</button></NuxtLink>
            </form>
                    </div>
        <div class="col">
        </div>

    </div>
</template>
<style scoped>
.ktgr {
    height: 300px;
    width: 100%;
    margin: 80px;
}

.navcon {
    height: 82px;
    background-color: rgb(0, 47, 255);
}
</style>
<script setup>
</script>