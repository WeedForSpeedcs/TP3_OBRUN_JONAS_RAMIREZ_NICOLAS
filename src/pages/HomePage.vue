<template>
  <div>
    <h2>Bienvenue sur la page d'accueil !</h2>
    <p>Voici quelques exemples de boutons :</p>
    <div class="button-group">
      <BaseButton>Bouton Primary (défaut)</BaseButton>
      <BaseButton disabled>Bouton Désactivé</BaseButton>
      <BaseButton color="warn">Bouton Warn</BaseButton>
      <BaseButton color="danger">Bouton Danger</BaseButton>
    </div>
  </div>
</template>

<script>
import BaseButton from '../components/BaseButton.vue'

export default {
  name: 'HomePage',
  components: {
    BaseButton,
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