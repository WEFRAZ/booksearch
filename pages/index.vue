<template>
    <div>
        <nav class="navbar ">
            <div class="container-fluid row text-center">
                <div class="cari col-10 m-2">
                    <form @submit.prevent="getData">
                        <input v-model="keyword" class="form-control me-2" type="search" placeholder="BUKU APA YANG ANDA CARI ?">
                    </form>
                </div>
                <div class="kembali col-1">
                    <NuxtLink to="/home/home" class="btn btn-dak col-2"><img src="~/assets/img/home.png" alt=""></NuxtLink>
                </div>
            </div>
        </nav>
        <div class="row">
            <div v-for="book in books" :key="book.id" class="col-2">
                <div class="card">
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