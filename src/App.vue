<template>
  <div id="app" class="section">
    <header-component></header-component>
    <router-view/>
    <footer-component></footer-component>
  </div>
</template>
<script>
import FooterComponent from './components/FooterComponent.vue'
import HeaderComponent from './components/HeaderComponent.vue'
export default {
  components: { FooterComponent, HeaderComponent },
  
}
</script>

    HeaderComponent