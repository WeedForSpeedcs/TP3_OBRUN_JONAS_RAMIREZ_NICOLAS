<template>
  <div>
    <h2>Bienvenue sur la page d'accueil !</h2>
    <p>Voici quelques exemples de boutons :</p>
    <div class="button-group">
      <BaseButton>Bouton Primary (défaut)</BaseButton>
      <BaseButton disabled>Bouton Désactivé</BaseButton>
      <BaseButton color="warn">Bouton Warn</BaseButton>
      <BaseButton color="danger">Bouton Danger</BaseButton>
      <AsyncButton :onClick="simulateAsyncClick">
        Désactivé et animé pendant 2 secondes si cliqué
      </AsyncButton>
    </div>
  </div>
</template>

<script>
import BaseButton from '../components/BaseButton.vue'
import AsyncButton from '../components/AsyncButton.vue'

export default {
  name: 'HomePage',
  components: {
    BaseButton,
    AsyncButton,
  },
  methods: {
    simulateAsyncClick() {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve();
        }, 2000);
      });
    },
  },
}
</script>

<style scoped>
.button-group {
  display: flex;
  gap: 1rem;
  margin-top: 1.5rem;
  flex-wrap: wrap;
  justify-content: center;
}
</style> 