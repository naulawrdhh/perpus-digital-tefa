<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form  @submit.prevent="getData">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Filter...">
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ data?.length }} dari {{ Totalpengunjung }}</div>
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
            <tr v-for="(visitor,i) in visitors" :key="i">
              <td>{{  i+1  }}.</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
              <td>{{ visitor.keperluan.nama}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <NuxtLink to="/">
      <button type="button" class="btn btn-primary">kembali</button>
    </NuxtLink>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const keyword = ref('')
const visitors = ref([])
const data = ref(visitors)
const Totalpengunjung =  ref(0) 

const getPengunjung = async () => {
    const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
    if(data) visitors.value = data
}
const getTotalpengunjung = async () => {
  const { count, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*)`, { count: 'exact', head: true })
  if (count) Totalpengunjung.value = count
}
const getData = async () => {
    const {data,error} = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
    .ilike('nama', `%${keyword.value}%`)
    if(data) visitors.value = data
}

onMounted(() => {
    getPengunjung()
    getData()
    getTotalpengunjung()
})
</script>
