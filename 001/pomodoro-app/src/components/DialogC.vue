<template>
   
    <v-dialog v-model="dialog" persistent max-width="600px" >
       <v-card>
          Eu sou um dialog
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
      }
   },

}
</script>

<style>

</style>