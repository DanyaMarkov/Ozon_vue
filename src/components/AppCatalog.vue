<template>

  <div class="catalog-button">
    <button>
      <span class="catalog-button_burger"></span><span class="catalog-button_text">Каталог</span>
    </button>
    <div class="catalog" :style="{display : this.isShowCatalog}">
      <ul class="catalog-list">
        <li>Игровая приставка</li>
        <li>Периферия для ПК</li>
        <li>Игры и софт</li>
      </ul>
    </div>
  </div>

</template>

<script>
export default {
  props: ['isShowCatalog'],
  data () {
    return {
    }
  },
  methods: {

  }
}
</script>
