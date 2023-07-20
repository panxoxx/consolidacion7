<template>
  <v-container>
    <v-row justify="center">
      <v-col md="10">  

       <modal-comp @close='dialog=false' :dialog='dialog'/>      
        
        <v-data-table
          
          :headers="headers"
          :items="cursos"
          sort-by="title"
          class="elevation-1"
        >
          <template v-slot:top>
            <v-toolbar flat>
             
              <v-divider class="mx-4" inset vertical></v-divider>
              <v-spacer></v-spacer>
            
              <v-dialog v-model="dialogDelete" max-width="500px">
                <v-card>
                  <v-card-title class="text-h5"
                    >¿Quires eliminarlo?</v-card-title
                  >
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="closeDelete"
                      >NO</v-btn
                    >
                    <v-btn color="blue darken-1" text @click="deleteItemConfirm"
                      >SI</v-btn
                    >
                    <v-spacer></v-spacer>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-toolbar>
          </template>
          <template v-slot:[`item.actions`]="{ item }">
           
             <v-icon small class="mr-2" @click="editar(item)">
              mdi-pencil
            </v-icon>
            <v-icon small @click="borrar(item)"> mdi-delete </v-icon>
          </template>
          
        </v-data-table>    
  
  <div>    
    <v-alert
      dense
      outlined
      color="green"
    > <v-icon color="green">mdi-account-multiple</v-icon>
      Cantidad de Alumnos permitidos <strong>{{countTotalCupos}}</strong>
    </v-alert>
  </div>

  <div>    
    <v-alert
      dense
      outlined
      color="blue"
    > <v-icon color="blue">mdi-account-check</v-icon>
     Cantidad de Alumnos inscritos: <strong>{{countTotalInscritos}}</strong>
    </v-alert>
  </div>

  <div>    
    <v-alert
      dense
      outlined
      color="green"
    > <v-icon color="green">mdi-account-multiple-plus</v-icon>
     Cantidad total de cupos restantes:<strong>{{countTotalCuposDisponibles}}</strong>
    </v-alert>
  </div>

  <div>    
    <v-alert
      dense
      outlined
      color="blue"
    > <v-icon color="blue">mdi-cancel</v-icon>
      Cantidad total de cursos terminados:<strong>{{countCursosTerminados}}</strong>
    </v-alert>
  </div>

  <div>    
    <v-alert
      dense
      outlined
      color="green"
    > <v-icon color="green">mdi-bell-ring</v-icon>
      Cantidad total de cursos activos<strong>{{countCursosNoTerminados}}</strong>
    </v-alert>
  </div>

  <div>    
    <v-alert
      dense
      outlined
      color="blue"
    > <v-icon color="blue">mdi-bell-ring</v-icon>
      Cantidad total de cursos:<strong>{{countCursos}}</strong>
    </v-alert>
  </div>
    

      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState, mapGetters } from "vuex";
import Modal from '@/components/Modal.vue'
export default {
  name: "Cart-view",
  // props: {},
  data: function () {
    return {
      
      dialogDelete: false,
      headers: [
        {
          text: 'Curso',
          align: 'start',
          sortable: false,
          value: 'nombre',
        },
        { text: 'Cupos', value: 'cupos' },
        { text: 'Inscritos', value: 'inscritos' },
        { text: 'Duración', value: 'duracion' },
        { text: 'Costo', value: 'costo' },
        { text: 'Terminado', value: 'completado' },
        { text: 'Fecha', value: 'fecha_registro' },
        { text: 'Acciones', value: 'actions', sortable: false },
      ],
      deleteId:null,
      
     
     
    };
  },
  computed: {
    ...mapState(['cursos']),
    ...mapGetters(['countTotalCupos', 'countTotalInscritos','countTotalCuposDisponibles','countCursos','countCursosNoTerminados','countCursosTerminados'])
    
  },
  methods: {

    
   

  },
  watch: {
    
  },
   components: {
    'modal-comp': Modal
   },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>