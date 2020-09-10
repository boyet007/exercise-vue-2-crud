<template>
  <v-app>
    <v-main>
      <v-layout>
        <v-container class="gray lighthen-5">
          <v-row>
            <v-col cols="12 text-center">
                <h2 class="subheading blue--text">Sisinfo PT. Maju Sejahtera</h2>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col col="8">
              <TablePegawai />
            </v-col>
          </v-row>
        </v-container>
      </v-layout>
    </v-main>
  </v-app>
</template>

<script>
  import TablePegawai from './components/TablePegawai.vue'
  export default {
    components: {
      TablePegawai,
    },
  }
</script>


<style>
    * {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
</style>
