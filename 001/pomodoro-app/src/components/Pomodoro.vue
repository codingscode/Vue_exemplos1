<template>
   <v-card class="mt-8" >
       <v-tabs v-model="timerType" >
          <v-tab v-for="tab in tabsTitles" :key="tab" >
              {{ tab }}
          </v-tab>
          <v-tabs-items v-model="timerType">
            <v-tab-item  >
                <v-card color="basil" class="pa-5" flat>
                    <h1 class="time" >00:00</h1>
                    <v-btn color="primary" >Iniciar</v-btn>
                    <v-btn>Parar</v-btn>
                    <v-btn>Reset</v-btn>
                </v-card>
            </v-tab-item>
          </v-tabs-items>
       </v-tabs>
   </v-card>
</template>

<script>
export default {
    data() {
        return {
            timerType: 0, tabsTitles: ['Pomodoro', 'Short Break', 'Long Break']
        }
    }
}
</script>

<style lang="sass" scoped >
.v-card
  width: 600px
.time
   font-size: 80px
   font-weight: 400
   text-align: center
   
</style>