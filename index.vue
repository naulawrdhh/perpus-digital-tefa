<template>
  <div class="container-fluid">
      <div class="row">
          <div class="col-lg-12">
              <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
              <nuxt-link to="../"><button type="submit" class="btn btn-lg rounded-5 px-5 bg-primary text-white" style="float: right; margin-bottom: 15px;">KEMBALI</button></nuxt-link>
              <div class="my-3">
                  <form @submit.prevent="getpengunjung">
                      <input v-model="keyword" type="search" class="form-control rounded-5"
                          placeholder="filter...">
                  </form>
              </div>
              <div class="my-3 text-muted">menampilkan 8 dari 24</div>
              <table class="table">
                  <thead>
                      <tr>
                          <td>#</td>
                          <td>NAMA</td>
                          <td>KEANGGOTAAN</td>
                          <td>WAKTU</td>
                          <td>KEPERLUAN</td>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="(visitor, i) in visitors" :key="i">
                          <td>{{ i+1 }}</td>
                          <td>{{ visitor.nama }}</td>
                          <td>{{ visitor.keanggotaan.nama }}</td>
                          <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
                          <td>{{ visitor.keperluan.nama }}</td>
                      </tr>
                  </tbody>
              </table>
          </div>
      </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const keyword = ref('')
const visitors = ref ([])

const getpengunjung = async () => {
  const {data,error} = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
      .ilike('nama', `%${keyword.value}%`)
  if(data) visitors.value = data
}
onMounted(() =>{
  getpengunjung()
})
</script>