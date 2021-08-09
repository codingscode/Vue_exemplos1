<template>
   
    <v-dialog v-model="dialog" persistent max-width="600px" >
       <v-card>
          Eu sou um dialog 
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