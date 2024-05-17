<template>
  <div>
    <h1>Selamat Datang di Toko Olahraga</h1>
    
    <button @click="Sports = 'LandSports'" class="btn btn-primary">Land sports</button>
    <button @click="Sports = 'WaterSports'" class="btn btn-primary">Water sports</button>
    
    <div class="Sports">
      <!-- Tampilkan daftar olahraga berdasarkan jenis olahraga yang dipilih -->
      <LandSports v-if="Sports === 'LandSports'" />
      <WaterSports v-if="Sports === 'WaterSports'" />
    </div>
    <button @click="handleClick" class="btn btn-primary">Klik Saya!</button> 
  </div>

</template>

<script>
import LandSports from './components/LandSports.vue';
import WaterSports from './components/WaterSports.vue';
import { ref } from 'vue'

const Sports = ref('')

export default {
  name: 'App',
  components: {
    LandSports,
    WaterSports,
  },
  data() {
    return {
      Sports: '', // Variabel untuk menyimpan jenis olahraga yang dipilih
      name: '', // Variabel untuk menyimpan nama yang dimasukkan oleh pengguna
    };
  },
  methods: {
  handleClick() {
    // Memunculkan pesan dengan menggunakan alert
    alert(`Terima kasih ${this.name}! Email Anda telah diterima.`);

    // Memancarkan event 'input-email' dengan nilai input nama yang dimasukkan
    this.$emit('input-email', this.name);
  },
},
}
</script>

<style scoped>
/* Gaya umum untuk halaman ini */
h1 {
  text-align: center;
  margin-bottom: 20px;
}

button {
  display: block;
  margin: 20px auto;
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049;
}
</style>
