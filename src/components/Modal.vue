<template>
    <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="red lighten-2"
          dark
          v-bind="attrs"
          v-on="on"
        >
          AGREGAR
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          FORMULARIO
        </v-card-title>

        <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field class=" ml-4 mr-4"
      v-model="nombre"
      label="Nombre"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="img"
      label="URL Imagen"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="cupos"
      label="Cupos"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="inscritos"
      label="Inscritos"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="duracion"
      label="Duración"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="fecha_registro"
      label="Fecha de registo"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="costo"
      label="Costo"
      required
    ></v-text-field>

    <v-text-field class=" ml-4 mr-4"
      v-model="descripcion"
      label="Descripción"
      required
    ></v-text-field>
 

    <v-btn
      :disabled="!valid"
      color="success"
      class=" ml-4 mr-4"
      @click="agregar"
    >
      AGREGAR
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>

    <v-btn
      color="warning"
      @click="resetValidation"
    >
      Reset Validation
    </v-btn>
  </v-form>

        

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="dialog = false"
          >
           
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
    name: 'modal-comp',
    // props: {},
    data: function(){
        return {
            valid: true,
            nombre: '',
            img:'',
            cupos:'',
            inscritos:'',
            duracion:'',
            fecha_registro:'',
            costo:'',
            descripcion:'',
            inscritosError: '',
      
      
      select: null,
      
        }
    },
    // computed: {},
    methods: {
        ...mapActions (['agregar_curso']),

         agregar () {      
            let curso={
            nombre:this.nombre,
            img:this.img,
            cupos:this.cupos,
            inscritos:this.inscritos,
            duracion:this.duracion,
            fecha_registro:this.fecha_registro,
            costo:this.costo,
            descripcion:this.descripcion,
            };
            this.agregar_curso(curso);
            this.dialog=false

      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
    
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>