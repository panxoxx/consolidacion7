<template>
    <v-container>
      <h1 class="text-center mt-4 black--text">
      Nuestros cursos
    </h1>
        <card-home></card-home>
    </v-container>
</template>

<script>
import CardHome from '@/components/CardHome.vue'


export default {
    name: 'Home-view',
    // props: {},
    data: function(){
        return {}
    },
    // computed: {},
    // watch: {},
    components: {
       'card-home': CardHome
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>