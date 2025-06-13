<template>
  <div>
    <h2>Bienvenue sur la page d'accueil !</h2>
    <p>Voici quelques exemples de boutons :</p>
    <div class="button-group">
      <BaseButton>Bouton Actif</BaseButton>
      <BaseButton disabled>Bouton Désactivé</BaseButton>
      <BaseButton style="background-color: blue;">Bouton Stylisé</BaseButton>
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