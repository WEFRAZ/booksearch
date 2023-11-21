<template>
    <div>
        
<nav class="navbar ">
            <div class="container-fluid row text-center">
                <nav class="navbar">
  <div class="container-fluid justify-content-center">
    <a class="navbar-brand justify-content-center" href="#"><h2 class=" text-light">BOOK SEARCH TOOL </h2><h6 class=" text-light">SMKN4 TASIKMALAYA</h6></a>
  </div>
</nav>
                <div class="cari col-11 ">
                    <form @submit.prevent="getData">
                        <input v-model="keyword" class="form-control me-2" type="search" placeholder="BUKU APA YANG ANDA CARI ?">
                    </form>
                </div>
                <div class="kembali col-1">
                    <NuxtLink to="/home/home" class="btn btn-dak col-2"><button type="button" class="btn btn-light">EXIT</button></NuxtLink>
                </div>
            </div>
        </nav>
        <div class="row justify-content-evenly">
            <div v-for="book in books" :key="book.id" class="col-sm-2">
                <div class="card m-3">
                    <div class="char-header">
                        
                        <NuxtLink :to="`/detail/${book.id}`">
                            <img :src="book.cover" alt="cover" class="cover">
                        </NuxtLink>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped>
.navbar {
    background-color: rgb(0, 47, 255);

}

.cover {
    width: 100%;
    height: 200px;
}
</style>


<script setup>
const superbase = useSupabaseClient()
const books = ref([])
const keyword = ref('');

onMounted(() => getData())

async function getData() {
    let { data, error } = await superbase
        .from('buku')
        .select(`cover,
        id,judul,penulis,penerbit,
        kategori(id),rak(kode)
        `)
        .ilike('judul', `%${keyword.value}%`)
    if (data) books.value = data
    if (error) throw error
}
</script>