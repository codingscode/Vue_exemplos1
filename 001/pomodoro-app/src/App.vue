<template>
  <v-app>
    <v-content>
      <Pomodoro />
    </v-content>
  </v-app>
</template>

<script>
import Pomodoro from './components/Pomodoro.vue'


export default {
    name: 'App',

    components: {
        Pomodoro
      
    },
    data: () => ({
      //
    }),
}
</script>
