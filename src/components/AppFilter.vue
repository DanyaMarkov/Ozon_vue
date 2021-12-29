<template>
  <div class="col-3 col-xl-2 d-none d-lg-block">
    <div class="filter">
      <div class="filter-title">
        <h5>Фильтр</h5>
      </div>
      <div class="filter-price">
        <div class="filter-price_title">
          Цена
        </div>

        <form>
          <div class="filter-price_range">
            <div class="filter-price_input-wrapper">
              <label for="min" class="filter-price_label">от</label>
              <input id="min" class="filter-price_input" v-model="minPrice" @input="getFilterGoods">
            </div>
            <div class="filter-price_input-wrapper">
              <label for="max" class="filter-price_label">до</label>
              <input id="max" class="filter-price_input" v-model="maxPrice" @input="getFilterGoods">
            </div>
          </div>
        </form>

      </div>
      <div class="filter-check" @click="discountChange">
        <label class="filter-check_label">
          <input type="checkbox" class="filter-check_checkbox" id="discount-checkbox">
          <input type="checkbox" class="filter-check_checkmark" v-model="discount">
          <span class="filter-check_label-text">Акция</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['filter-goods'],
  data () {
    return {
      maxPrice: '',
      minPrice: '',
      discount: false
    }
  },

  methods: {
    async getFilterGoods () {
      const response = await fetch('https://ozon-v-default-rtdb.firebaseio.com/goods.json')
      let data = await response.json()
      data = this.hotSaleFilter(data)
      console.log('До фильтрации по ценам', data)

      if (this.minPrice === '' && this.maxPrice === '') {
        const filterData = data
        this.$emit('filter-goods', filterData)
        console.log('После выборки по ценам', filterData)
      } else if (this.minPrice !== '' && this.maxPrice !== '') {
        const filterData = data.filter((good) => {
          return good.price > +this.minPrice && good.price < +this.maxPrice
        })
        this.$emit('filter-goods', filterData)
        console.log('После выборки по ценам', filterData)
      } else if (this.minPrice !== '' && this.maxPrice === '') {
        const filterData = data.filter((good) => {
          return good.price > +this.minPrice
        })
        this.$emit('filter-goods', filterData)
        console.log('После выборки по ценам', filterData)
      } else if (this.minPrice === '' && this.maxPrice !== '') {
        const filterData = data.filter((good) => {
          return good.price < +this.maxPrice
        })
        this.$emit('filter-goods', filterData)
        console.log('После выборки по ценам', filterData)
      }
    },

    discountChange () {
      this.discount = !this.discount
      this.getFilterGoods()
    },

    hotSaleFilter (data) {
      const filterData = data.filter((good) => {
        return good.sale === this.discount
      })
      return filterData
    }
  }

}
</script>
