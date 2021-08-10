<template>
   <v-card class="mt-8" >
       <v-tabs @change="alterarTimerType" v-model="timerAtual" grow >
          <v-tab v-for="cronometro in cronometros" :key="cronometro.nome" >
              {{ cronometro.nome }}
          </v-tab>

       </v-tabs>

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
               <v-btn @click="resetar(cronometros[timerAtual].minutos)" :disabled="estaExecutando" >
                   <v-icon left small>mdi-restart</v-icon>
                   Reset
               </v-btn>
           </div>
       </v-card>
       <DialogC :cronometros="cronometros" :dialog="dialog" :fecharDialog="fecharDialog" :salvar="salvar" />
       
   </v-card>
</template>

<script>
import DialogC from './DialogC.vue'

export default {
    components: {
        DialogC
    },
    props: {
       dialog: {
          type: Boolean, required: true
       },
       fecharDialog: {
          type: Function, required: true
       }
    },
    data() {
        return {
           estaExecutando: false, 
           timerInstance: null,
           totalSegundos: 25*60,
           timerAtual: 0, 
           cronometros: [ 
               {nome: 'Pomodoro', minutos: 25},
               {nome: 'Curto', minutos: 5},
               {nome: 'Longo', minutos: 10}
            ]
            
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
                if (this.totalSegundos <= 0) {
                   this.parar()
                   return
                }
                this.totalSegundos -= 1
            }, 1000)
        },
        parar() {
            this.estaExecutando = false
            clearInterval(this.timerInstance)

        },
        resetar(minutos) {
            this.parar()
            this.totalSegundos = minutos*60
        },
        alterarTimerType(num) {
            console.log(num)
            this.timerAtual = num
            this.resetar(this.cronometros[num].minutos)
        },
        salvar() {
            this.fecharDialog()
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