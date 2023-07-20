<template>
  <v-container>
    <v-row class="d-flex justify-center mt-3">
      <v-col
        cols="12"
        sm="6"
        md="3"
        my-3
        v-for="curso in cursos"
        :key="curso.id"
      >
        <v-card width="400" height="700">
          <v-img align-center height="200"   :src="curso.img">
            <v-app-bar flat color="rgba(0, 0, 0, 0)">
              <v-spacer></v-spacer>
              <v-btn color="white" icon> </v-btn>
            </v-app-bar>
          </v-img>
          <v-card-title class="black--text mt-8">
            <p class="ml-3">
              {{ curso.nombre }}
            </p>
          </v-card-title>
          <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">Información</div>

            <v-timeline align-top dense>
              <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    Costo:<strong>{{ curso.costo }}</strong>
                  </div>
                    Duración:<strong>{{ curso.duracion }}</strong>
                  </div>
              </v-timeline-item>

              <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    Cupos:<strong>{{ curso.cupos }}</strong>
                  </div>
                    Completado:<strong>{{ curso.completado }}</strong>
                  </div>
              </v-timeline-item>

              <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    Fecha de Registro:
                  </div>
                  <div><strong>{{ curso.fecha_registro}}</strong></div>                    
                </div>
              </v-timeline-item>

               <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    Descripción:
                  </div>
                  <div><strong>{{ curso.descripcion.slice(0,200)}}</strong></div>                    
                </div>
              </v-timeline-item>



            </v-timeline>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "component-name",
  // props: {},
  data: function () {
    return {};
  },
  computed: {
    ...mapState(["cursos"]),
  },
  //methods: {}
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>