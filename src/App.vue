<template>

    <app-header
    ></app-header>

    <main>
      <div class="container">
        <div class="row">

          <app-filter></app-filter>

          <!-- Goods -->
          <div class="col-12 col-lg-9 col-xl-10">
            <div class="container">
              <div class="row no-gutters goods">

                <app-good :goods="goods"></app-good>

              </div>
            </div>
          </div>
          <!-- Goods -->

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
      goods: []
    }
  },
  mounted () {
    this.getGoods()
  },
  methods: {
    getGoods () {
      fetch('https://ozon-v-default-rtdb.firebaseio.com/goods.json')
        .then(response => response.json())
        .then(data => {
          this.goods = data
        })
    }
  },
  components: { AppHeader, AppGood, AppFilter }
}
</script>

<style lang="scss">

</style>
