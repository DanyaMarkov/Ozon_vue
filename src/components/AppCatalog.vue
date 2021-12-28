<template>

  <div class="catalog-button">
    <button>
      <span class="catalog-button_burger"></span><span class="catalog-button_text">Каталог</span>
    </button>
    <div class="catalog" :style="{display : isShowCatalog}">
      <ul class="catalog-list">
        <li
          v-for="item in categories"
          :key="item.category"
          @click="getCategoryGoods(item.category)">
          {{item.category}}
        </li>
      </ul>
    </div>
  </div>

</template>

<script>
export default {
  emits: ['category-goods'],
  props: ['isShowCatalog', 'categories'],
  data () {
    return {
    }
  },
  methods: {
    async getCategoryGoods (type) {
      const response = await fetch('https://ozon-v-default-rtdb.firebaseio.com/goods.json')
      const data = await response.json()
      const filterData = data.filter((good) => {
        return good.category === type
      })
      this.$emit('category-goods', filterData)
    }
  }
}
</script>
