<template>
    <div>
        
        <div v-if="loading">
            <center>
            <h3>sedang memuat</h3>
             <div class="loader"></div>
            </center>
        </div>
        <div v-else>
            <nav class="navbar">
                <div class="container-fluid">
                    <a class="navbar-brand">DETAIL BUKU  :  {{ book.judul }}</a>
                    <form class="d-flex" role="search">
                        <NuxtLink to="/" class="btn btn-dak"><button type="button" class="btn-close btn-close-black"
                aria-label="Close"></button></NuxtLink>
                    </form>
                </div>
            </nav>
            <div class="con1">
                <table style="width: 70%;">
                    <tr>
                        <td rowspan="8"><img :src="book.cover" alt="cover" class="cover" style="margin: 30px;"></td>
                        <td>
                            JUDUL
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.judul }}
                        </td>
                    </tr>
                    <tr>
                        <td>PENULIS</td>
                        <td>
                            :
                        </td>
                        <td> {{ book.penulis }}</td>
                    </tr>
                    <tr>
                        <td>
                            PENERBIT
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.penerbit }}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            TAHUN TERBIT
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.tahun_terbit }}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            KATEGORI
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.kategori.nama }}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            KODE RAK
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.rak.kode }}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            DESKRIPSI
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.deskripsi }}
                        </td>
                    </tr>
                    <tr>
                        <td>
                            NO ISBN
                        </td>
                        <td>
                            :
                        </td>
                        <td>
                            {{ book.no_isbn }}
                        </td>
                    </tr>
                </table>
            </div>

        </div>

    </div>
</template>

<script setup>
const route = useRoute()
const id = route.params.id
const superbase = useSupabaseClient()
const book = ref([])
console.log(id)
const loading = ref(true)

onMounted(() => getData())

async function getData() {
    loading.value = true
    let { data, error } = await superbase
        .from('buku')
        .select(`
            id,judul,penulis,penerbit,
            kategori(id, nama),rak(kode),tahun_terbit, cover,deskripsi,no_isbn
            `)
        .eq("id", id)
    if (data) {
        book.value = data[0]
        loading.value = false
    }
    if (error) throw error
}
</script>


<style scoped>
.cover {
    width: 250px;
    height: 350px;
}

.con1 {
    width: 100%;
}
.navbar{
    background-color: rgb(0, 47, 255) ;
}
.loader {
  border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid blue;
  border-bottom: 16px solid blue;
  width: 100px;
  height: 100px;
  -webkit-animation: spin 2s linear infinite;
  animation: spin 2s linear infinite;
}

@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>