<template>

    <app-header
    ></app-header>

    <main>
      <div class="container">
        <div class="row">

          <app-filter></app-filter>
          <app-good></app-good>

        </div>
      </div>
    </main>

</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppGood from './components/AppGood.vue'
import AppFilter from './components/AppFilter.vue'

export default {
  name: 'App',
  data () {
    return {
    }
  },
  components: { AppHeader, AppGood, AppFilter }
}
</script>

<style lang="scss">

</style>
