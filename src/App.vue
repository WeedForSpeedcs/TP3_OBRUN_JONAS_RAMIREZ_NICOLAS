<template>
  <div class="app-container">
    <base-header />
    <main class="main-content">
      <home-page />
    </main>
    <base-footer />
  </div>
</template>

<script>
import HomePage from './pages/HomePage.vue'
import BaseHeader from './components/BaseHeader.vue'
import BaseFooter from './components/BaseFooter.vue'

export default {
  name: 'App',
  components: {
    HomePage,
    BaseHeader,
    BaseFooter
  }
}
</script>

<style scoped>
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, #f8fafc 0%, #e0f7fa 100%);
}
.main-content {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.main-content > * {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 24px rgba(66, 185, 131, 0.08);
  padding: 2rem 3rem;
  min-width: 320px;
  max-width: 600px;
  width: 100%;
}
</style>
