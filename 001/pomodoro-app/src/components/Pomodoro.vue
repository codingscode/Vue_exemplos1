<template>
   <v-card class="mt-8" >
       <v-tabs v-model="timerType" grow >
          <v-tab v-for="tab in tabsTitles" :key="tab" >
              {{ tab }}
          </v-tab>
          <v-tabs-items v-model="timerType">
            <v-tab-item  >
                <v-card color="basil" class="pa-5 d-flex flex-column justify-center align-center" flat>
                    <h1 class="time" >{{mostrarMinutos}}:{{mostrarSegundos}}</h1>
                    <div class="button-group" >
                        <v-btn color="primary" >
                            <v-icon left small>mdi-play-circle-outline</v-icon>
                            Iniciar
                        </v-btn>
                        <v-btn color="error" >
                            <v-icon left small>mdi-stop-circle-outline</v-icon>
                            Parar
                        </v-btn>
                        <v-btn>
                            <v-icon left small>mdi-restart</v-icon>
                            Reset
                        </v-btn>
                    </div>
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
           mostrar: {
              minutos: '00', segundos: '00',
           },
           totalSegundos: 25*60,
           timerType: 0, tabsTitles: ['Pomodoro', 'Short Break', 'Long Break']
        }
    },
    computed: {
        mostrarMinutos() {
           const minutos = Math.floor(this.totalSegundos / 60)
           return this.tempoFormato(minutos)
        },
        mostrarSegundos() {
           const segundos = this.totalSegundos % 60
           return this.tempoFormato(segundos)
        }
    },
    methods: {
        tempoFormato(time) {
           if (time < 10) {
              return '0' + time
           }
           return time.toString()
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

.v-btn
   margin: 0 2px
   
</style>