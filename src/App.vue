<template>

    <app-header
      v-on:search-goods="searchGoods"
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
      // categories: [],
    }
  },
  mounted () {
    this.getGoods()
  },
  methods: {
    async getGoods () {
      const response = await fetch('https://ozon-v-default-rtdb.firebaseio.com/goods.json')
      const data = await response.json()
      this.goods = data
    },

    searchGoods (data) {
      this.goods = data
    }

    // getCategories() {
    //   this.categories = this.goods.filter(good => good.category === "Игры и софт");
    //   console.log(this.categories)
    // }

  },
  provide () {
    return {
      goods: this.goods
    }
  },
  components: { AppHeader, AppGood, AppFilter }
}
</script>

<style lang="scss">

</style>
