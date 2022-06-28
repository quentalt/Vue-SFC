<template>
	<div>
		<SaisieTexte 
			v-model="libelleNouvelleTache"
			placeholder="Nouvelle tache pour les newbies"
			@keydown.enter="ajoutTache"
		/>
		<SaisieDetail 
			v-model="libelleDetail" 
			@keydown.enter="ajoutTache"
		/>
		<p v-if="listeTaches.length">
			<TacheDetaillee
				v-for="uneTache in listeTaches"
				:key="uneTache.id"
				:uneTache="uneTache"
				@suppression="supprimeTache"
			/>
		</p>
		<p v-else>
			Plus aucune tache en cours. Vous devriez en ajouter !.
		</p>
	</div>
</template>

<script>
import SaisieTexte from './SaisieTexte.vue'
import SaisieDetail from './SaisieDetail.vue'

import TacheDetaillee from './TacheDetaillee.vue'

let prochaineTacheId = 1

export default {
	components: {
		SaisieTexte, TacheDetaillee, SaisieDetail
	},
  data () {
    return {
	libelleNouvelleTache: '',
	libelleDetail: '',
    listeTaches: [
				{
					id: prochaineTacheId++,
					text: 'Apprendre Vue',
					libelle: 'La partie Data est fondamentale pour le développement logiciel. Une application doit tenir la charge, la volumétrie et être capable d assurer la persistence des données'
				},
				{
					id: prochaineTacheId++,
					text: 'Utiliser des composants SFC',
					libelle: ''
				},
				{
					id: prochaineTacheId++,
					text: 'Apprendre les tests unitaires',
					libelle: ''
				}
			]
    }
  },
	methods: {
		ajoutTache () {
			const trimmedText = this.libelleNouvelleTache.trim()
			const detail = this.libelleDetail.trim()
			if (trimmedText) {
				this.listeTaches.push({
					id: prochaineTacheId++,
					text: trimmedText,
					libelle: detail
				})
				this.libelleNouvelleTache = ''
				this.libelleDetail= ''
			}
		},
		supprimeTache (idAEnlever) {
			this.listeTaches = this.listeTaches.filter(uneTache => {
				return uneTache.id !== idAEnlever
			})
		}
	}
}
</script>