<template>
  <textarea
    type="text"
    class="input"
    :value="value"
    v-on="listeners"
    rows="5" cols="50"
  ></textarea>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    }
  },
  computed: {
    listeners () {
      return {
        // On passe en entree tous les composants qui écoutent des évènements 
        ...this.$listeners,
        // Surcharge du listener (écouteur) input pour qu'il fonctionne avec la directive v-model
        input: event => this.$emit('input', event.target.value)
      }
    }
  }
}
</script>
