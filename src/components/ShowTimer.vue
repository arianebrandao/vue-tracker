<template>
  <section>
    <strong>{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ShowTimer',
  //tudo que recebe do componente pai
  props: {
    tempoEmSegundos: {
      type: Number,
      default: 0,
    }
  },
  //monitora informação e atualiza quando é alterada
  computed: {
    tempoDecorrido() : string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
    }
  },
})
</script>

