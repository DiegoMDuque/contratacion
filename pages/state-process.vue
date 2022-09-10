<template>
  <v-container>
    <!-- Title Page  -->
    <div class="pa-0 title d-flex flex-wrap mb-5 justify-center">
      <p class="d-flex text-overline justify-center">
        ESTADO DEL PROCESO
      </p>
    </div>

    <!-- Button Add  -->
    <div>
      <v-row>
        <v-col class="d-flex justify-start">
          <v-btn
            color="primary"
            dark
            small
            class="mb-2 text-capitalize"
            title="Crear Nuevo"
            @click="dialogCreate = true"
          >
            Añadir
            <v-icon>mdi-plus</v-icon>
          </v-btn>
        </v-col>
      </v-row>
    </div>

    <!-- Table -->
    <div>
      <v-data-table :headers="headers" :items="dataItems" class="elevation-1">
        <template v-slot:[`item.actions`]="{ item }">
          <v-icon small class="mr-2" @click="viewItem(item)"> mdi-eye </v-icon>
          <v-icon small class="mr-2" @click="editItem(item)">
            mdi-pencil
          </v-icon>
          <v-icon small class="mr-2" @click="deleteItem(item)">
            mdi-delete
          </v-icon>
        </template>
      </v-data-table>
    </div>

    <!-- Dialog created -->
    <v-dialog v-model="dialogCreate" max-width="500">
      <v-card>
        <v-card-title class="d-flex text-overline justify-center"
          >Crear registro</v-card-title
        >
        <v-card-text>
          <v-row>
            <v-col cols="12" md="12" sm="12">
              <v-text-field label="Nombre" outlined dense></v-text-field>
            </v-col>
            <v-col cols="12" md="6" sm="12">
              <v-select label="Proceso" :items="stateAgroup" outlined dense></v-select>
            </v-col>
            <v-col cols="12" md="6" sm="12">
              <v-select label="Estado" :items="state" outlined dense></v-select>
            </v-col>
          </v-row>
        </v-card-text>
        <v-card-actions></v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Dialog read -->
    <v-dialog v-model="dialogRead">
      <v-card>
        <v-card-title></v-card-title>
        <v-card-text></v-card-text>
        <v-card-actions></v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Dialog update -->
    <v-dialog v-model="dialogUpdate">
      <v-card>
        <v-card-title></v-card-title>
        <v-card-text></v-card-text>
        <v-card-actions></v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Dialog confirm delete -->
    <v-dialog v-model="dialogDelete">
      <v-card>
        <v-card-title></v-card-title>
        <v-card-text></v-card-text>
        <v-card-actions></v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      dialogCreate: false,
      dialogRead: false,
      dialogUpdate: false,
      dialogDelete: false,
      headers: [
        {
          text: "ID",
          align: "start",
          sortable: false,
          value: "id",
        },
        {
          text: "NOMBRE",
          align: "start",
          sortable: false,
          value: "nombre",
        },
        {
          text: "PROCESO",
          align: "start",
          sortable: false,
          value: "proceso",
        },
        {
          text: "ESTADO",
          align: "start",
          sortable: false,
          value: "estado",
        },
        {
          text: "ORDEN",
          align: "start",
          sortable: false,
          value: "orden",
        },
        {
          text: "ACCIONES",
          sortable: false,
          value: "actions",
        },
      ],
      dataItems: [
        {
          id: 1,
          nombre: "COMITÉ DE CONTRATACIÓN",
          proceso: "Precontractual",
          estado: "1",
          orden: '02',
        },
        {
          id: 1,
          nombre: "PUBLICADO",
          proceso: "Precontractual",
          estado: "1",
          orden: '03',
        },
        {
          id: 1,
          nombre: "LEGALIZADO",
          proceso: "Contractual",
          estado: "1",
          orden: '09',
        },
      ],
      stateAgroup: ["Contractual", "Precontractual"],
      state: ["Activo", "Inactivo"]
    };
  },
  methods: {},
};
</script>