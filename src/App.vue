<template>
    <main>
      <app-header></app-header>
      <router-view></router-view>
      <app-footer></app-footer>
    </main>
</template>

<script>
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
  export default {
    components:{
     appHeader: Header,
     appFooter: Footer
    },
    data () {
      return {
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'bubble_chart', title: 'Inspire' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify.js'
      }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
</style>