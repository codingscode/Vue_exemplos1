<template>
   
    <v-dialog v-model="dialog" persistent max-width="600px" >
       <v-card>
         <v-card-title>
            <span class="headline">Configurações</span>
         </v-card-title>
         <v-card-text>
            <v-text-field v-for="(crono, i) in cronometrosAtualizados" :key="i" label="Pomodoro" v-model="cronometrosAtualizados[i]" />
         </v-card-text>
         <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="fecharDialog" >
              Fechar
            </v-btn>
            <v-btn color="blue darken-1" text @click="salvar" >
              Salvar
            </v-btn>
         </v-card-actions>
       </v-card>

    </v-dialog>
</template>

<script>
export default {
   props: {
      dialog: {
         type: Boolean, required: true
      },
      fecharDialog: {
         type: Function, required: true
      },
      salvar: {
         type: Function, required: true
      },
      cronometros: {
         type: Array, required: true
      }
   },
   data() {
      return {
         cronometrosAtualizados: []
      }
   },
   mounted() {
      this.cronometrosAtualizados = this.cronometros.map((cada) => {
         return cada.minutos
      })
   }

}
</script>

<style>

</style>