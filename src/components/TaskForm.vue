<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TimerController @aoTemporizadorFinalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerController from './TimerController.vue'

export default defineComponent({
  name: "TaskForm",
  // componentes filhos
  components: {
    TimerController,
  },
  data () {
    return {
      descricao: '',
    }
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number) : void {
      console.log('tempo da tarefa', tempoDecorrido)
      console.log('descricao da tarefa', this.descricao)

      this.descricao = ''
    }
  }
});
</script>

<style scoped></style>
