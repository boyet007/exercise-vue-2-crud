<template>
  <v-card class="elevation-12">
    <v-toolbar color="primary">
      <v-toolbar-title class="white--text">Tabel Pegawai</v-toolbar-title>
    </v-toolbar>
    <v-card-text>
      <v-data-table 
        :headers="headers"
        :items="employeers"
        sort-by="id"
        class="elevation-1"
      >
        <template v-slot:top>
          <v-toolbar flat color="white">
            <v-toolbar-title>Input Data</v-toolbar-title>
             <v-spacer></v-spacer>
            <v-dialog v-model="dialog" max-width="600px">
              <template v-slot:activator="{ on, attrs }">
                <v-btn color="info" dark v-bind="attrs" v-on="on">Tambah</v-btn>
              </template>
              <v-card>
                <v-card-title>
                  <span class="headline">{{ formTitle }}</span>
                </v-card-title>
                <v-card-text>
                  <v-container>
                    <v-row>
                      <v-col cols="12">
                        <v-text-field v-model="editedItem.nama" label="Nama"></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field v-model="editedItem.nama" label="Posisi"></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field v-model="editedItem.nama" label="Jenkel"></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn color="green darken-1" text @click="simpan">Simpan</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-toolbar>
        </template>
        <template v-slot:[`item.aksi`]="{ item }">
             <v-icon
              small
              @click="editItem(item)"
            >
              mdi-pencil
            </v-icon>
            <v-icon
              small
              @click="deleteItem(item)"
            >
              mdi-delete
            </v-icon>
        </template>
      </v-data-table>
    </v-card-text>
    </v-card>
</template>

<script>
import { AIRTABLE_URL, AIRTABLE_API_KEY } from '@/settings/airtable'
export default {
  data: () => ({
    dialog: false,
    editedIndex: -1,
    employeers: [],
    headers: [
      { text: 'Id', value: 'id' },
      { text: 'Nama', value: 'nama' },
      { text: 'Posisi', value: 'posisi' },
      { text: 'Jenkel', value: 'jenkel' },
      { text: 'Aksi', value: 'aksi' },
    ],
    editedItem: {
      nama: '',
      posisi: '',
      jenkel: '',
    },
  }),
     mounted() {
      this.$http.get(AIRTABLE_URL, {
        headers: {
          Authorization : `Bearer ${ AIRTABLE_API_KEY }`
        }
      })
      .then((res) => {
        this.employee = []
        this.employeers = res.data.records.map((employee) => {
          return {
            id: employee.id,
            ...employee.fields
          }
        });
      })
      .catch((err) => {
        console.log(err)
      })
    },
  methods: {
    simpan () {
      alert('simpan');
    },
    editItem (item) {
      console.log(item)
    },
    deleteItem (item) {
      console.log(item)
    },
  },
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Tambah Data' : 'Edit Data'
    }
  }
}
</script>