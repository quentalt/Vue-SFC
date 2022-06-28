<template>
  <Competence :titre="uneTache.id" :contenu="uneTache.text"> 
    <template slot="detail">
    {{ uneTache.libelle }}
    </template>
  </Competence>
         
</template>


<script>
import Competence from './Competence.vue'

export default {
  components: {
    Competence 
  },
  props: {
    uneTache: {
      type: Object,
      required: true
    }
  }
}
</script>