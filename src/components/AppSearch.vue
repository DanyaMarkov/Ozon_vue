<template>
    <div class="search">
      <div class="search-wrapper">
        <input class="search-wrapper_input" type="text" v-model="inputValue" :placeholder="placeholderString" @input="getSearchGoods"  />
        {{inputValue}}
      </div>
      <div class="search-btn">
        <button></button>
      </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      inputValue: '',
      placeholderString: 'Найти...'
    }
  },
  methods: {
    async getSearchGoods () {
      const response = await fetch('https://ozon-v-default-rtdb.firebaseio.com/goods.json')
      const data = await response.json()
      const filterData = data.filter((good) => {
        return good.title.includes(this.inputValue)
      })
      this.$emit('search-goods', filterData)
    }
  }

}
</script>
