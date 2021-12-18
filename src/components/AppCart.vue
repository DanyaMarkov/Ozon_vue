<template>
    <div class="cart" :style="{display : this.isShowCart}">
      <div class="cart-body">
        <div class="cart-title">Корзина</div>
        <div class="cart-total">Общая сумма: <span>0</span> руб</div>

        <div class="cart-wrapper">
          <div id="cart-empty">
            Ваша корзина пока пуста
          </div>
        </div>
        <button class="btn btn-primary cart-confirm">Оформить заказ</button>
        <div class="cart-close" @click="closeCart">
        </div>
      </div>
    </div>
</template>

<script>
export default {
  props: ['isShowCart'],
  emits: ['close-cart'],
  data () {
    return {
    }
  },
  methods: {
    closeCart () {
      this.$emit('close-cart', 'none')
    }
  }
}
</script>
