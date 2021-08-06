<template>
   <v-card class="mt-8" >
       <v-tabs @change="alterarTimerType" v-model="timerType" grow >
          <v-tab v-for="tab in tabsTitles" :key="tab" >
              {{ tab }}
          </v-tab>
          <v-tabs-items v-model="timerType">
            <v-tab-item  >
                <v-card color="basil" class="pa-5 d-flex flex-column justify-center align-center" flat>
                    <h1 class="time" >{{mostrarMinutos}}:{{mostrarSegundos}}</h1>
                    <div class="button-group" >
                        <v-btn color="primary" @click="iniciar" >
                            <v-icon left small>mdi-play-circle-outline</v-icon>
                            Iniciar
                        </v-btn>
                        <v-btn color="error" @click="parar" >
                            <v-icon left small>mdi-stop-circle-outline</v-icon>
                            Parar
                        </v-btn>
                        <v-btn @click="resetar" :disabled="estaExecutando" >
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
           estaExecutando: false, 
           timerInstance: null,
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
        },
        iniciar() {
            this.parar()
            this.estaExecutando = true
            this.timerInstance = setInterval(() => {
                this.totalSegundos -= 1
            }, 1000)
        },
        parar() {
            this.estaExecutando = false
            clearInterval(this.timerInstance)

        },
        resetar() {
            this.parar()
            this.totalSegundos = 25*60
        },
        alterarTimerType(num) {
            console.log(num)
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