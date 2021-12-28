<template>

    <app-header
      :categories="categories"

      v-on:search-goods="searchGoods"
      v-on:category-goods="categoryGoods"
    ></app-header>

    <main>
      <div class="container">
        <div class="row">

          <app-filter
            v-on:filter-goods="filterGoods"
            v-on:discount-goods="discountGoods"
          ></app-filter>

          <!-- Goods -->
          <div class="col-12 col-lg-9 col-xl-10">
            <div class="container">
              <div class="row no-gutters goods">

                <h2 v-if="goods.length == 0" class="goods-notion">По такому зарпосу товары не найдены</h2>
                <app-good v-else :goods="goods"></app-good>

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
      goods: [],
      categories: []
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
      this.getCategories()
    },

    searchGoods (data) {
      this.goods = data
    },

    categoryGoods (data) {
      this.goods = data
    },

    getCategories () {
      const obj = {}
      let newArr = []
      this.goods.forEach(function (v) {
        obj[v.category] = v
      })
      newArr = Object.keys(obj).map(function (id) {
        return obj[id]
      })
      this.categories = newArr
    },

    filterGoods (data) {
      this.goods = data
    },

    discountGoods (data) {
      this.goods = data
    }

  },
  components: { AppHeader, AppGood, AppFilter }
}
</script>

<style lang="scss">
  .goods-notion {
    margin: 50px auto;
  }
</style>
