<script setup lang="ts">
import { ref } from 'vue'

const kodePerbaikan = ref('')

const kirim = () => {
  // create array from string by splitting on new line or space
  const kodePerbaikanArray = kodePerbaikan.value.split(/\n| /)      
  // remove empty strings
  const kodePerbaikanArrayFiltered = kodePerbaikanArray.filter((kode) => kode !== '')
  // remove duplicates
  const kodePerbaikanArrayFilteredUnique = [...new Set(kodePerbaikanArrayFiltered)]
  
  console.log(kodePerbaikanArrayFilteredUnique)
}

</script>


<template>
  <v-container>
    <v-img width="100" src="@/assets/logo.png"></v-img>
      <v-row>
        <v-col cols="12" md="6">
          <v-img src="@/assets/repair.svg"></v-img>
        </v-col>
        <v-col class="mt-16">
          <h1>Lacak Perbaikan</h1>
          <p class="my-5">Masukkan <b>maksimal sampai dengan 20 Kode Perbaikan</b> 
            hanya dengan menyalinnya ke sini (dipisah dengan spasi atau enter), semua otomatis terurut</p>
          <v-textarea
          prepend-inner-icon="mdi-barcode-scan"
          rows="10" 
          v-model="kodePerbaikan"
          placeholder="Masukkan kode Perbaikan di sini. Contoh:
EM.XXXXXXXXXX-20XXXXXX-X-XXXXXX
EM.XXXXXXXXXX-20XXXXXX-X-XXXXXX
EM.XXXXXXXXXX-20XXXXXX-X-XXXXXX"
          class="mt-10"
          ></v-textarea>
          <v-btn
          @click="kirim"
          size="large"
          color="primary"
          >
            Lacak Perbaikan
          </v-btn>
        </v-col>
      </v-row>
  </v-container>
</template>

