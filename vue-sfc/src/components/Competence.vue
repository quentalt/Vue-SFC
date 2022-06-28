<template>
    <article class="message" v-show="voirCompetence">
        <div class="message-header">
        {{ titre }}
        <button type="button" @click="voirCompetence = false">x</button>
        </div>
        <div class="message-body">
        {{ contenu }}
        <button @click="montreDetail=true"> Voir les détails</button>
        <div>
        <Modal v-if="montreDetail" @close="montreDetail = false">
        <slot name="detail"> </slot>
        </Modal>
        </div></div>
        </article>
</template>


<script>
import Modal from './Modal.vue'
export default {
    components: {
    Modal 
  },
  props: ['titre','contenu'],
    data() {
        return {
            voirCompetence: true,
            montreDetail: false
        }
    }
}
</script>