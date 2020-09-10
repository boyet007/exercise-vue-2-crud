<template>
    <v-card class="elevation-12">
        <v-toolbar color="warning">
            <v-toolbar-title>Input Pegawai</v-toolbar-title>
        </v-toolbar>
        <v-card-text>
            <v-form>
                <v-text-field v-model="nama" 
                    prepend-icon="mdi-map-marker"
                    label="Nama">

                </v-text-field>
           </v-form>
        </v-card-text>
    </v-card>
</template>

<script>
export default {
    data() {
        return {
            nama: '',
            posisi: '',
            jenkel: '',
        }
    }
}
</script>