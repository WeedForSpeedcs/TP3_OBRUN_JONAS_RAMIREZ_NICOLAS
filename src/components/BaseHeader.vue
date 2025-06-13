<template>
  <header class="header">
    <nav>
      <a href="#" class="home-link">
        <font-awesome-icon :icon="['fas', 'home']" /> Accueil
      </a>
    </nav>
    <div class="user">
      <font-awesome-icon :icon="['fas', 'user']" /> not yet login
    </div>
  </header>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faHome, faUser } from '@fortawesome/free-solid-svg-icons'

library.add(faHome, faUser)

export default {
  name: 'BaseHeader',
  components: {
    FontAwesomeIcon
  }
}
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #42b983;
  color: white;
  padding: 1rem;
}
.home-link {
  color: white;
  text-decoration: none;
  font-weight: bold;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  gap: 0.4em;
}
.user {
  font-style: italic;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  gap: 0.4em;
}
</style> 