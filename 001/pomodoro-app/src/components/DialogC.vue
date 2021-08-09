<template>
   
    <v-dialog v-model="dialog" persistent max-width="600px" >
       <v-card>
          Eu sou um dialog
         <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false" >
              Fechar
            </v-btn>
            <v-btn color="blue darken-1" text @click="dialog = false" >
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
      }
   }
}
</script>

<style>

</style>