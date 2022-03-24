<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <ShowTimer :tempoEmSegundos="tempoEmSegundos" />

    <PlayerButton
      @clicado="start"
      icone="fas fa-play"
      texto="play"
      :desabilitado="cronometroRodando"
    />
    <PlayerButton
      @clicado="stop"
      icone="fas fa-stop"
      texto="stop"
      :desabilitado="!cronometroRodando"
    />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import ShowTimer from "./ShowTimer.vue";
import PlayerButton from './PlayerButton.vue'

export default defineComponent({
  name: "TimerController",
  //emitir eventos
  emits: ["aoTemporizadorFinalizado"],
  components: {
    ShowTimer,
    PlayerButton,
  },
  //estado inicial do component
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },
  //funcoes que esse componente executa
  methods: {
    start() {
      //começar contagem
      //1s = 1000 ms
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    stop() {
      this.cronometroRodando = false;
      clearInterval(this.cronometro);
      this.$emit("aoTemporizadorFinalizado", this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    },
  },
});
</script>
