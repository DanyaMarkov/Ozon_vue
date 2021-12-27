<template>
      <header>
      <nav>
        <div class="container">
        <div class="row">
          <div class="col">
          <div class="navbar-wrapper d-flex justify-content-between align-items-center">
            <a class="logo" href="/"></a>
            <div class="d-flex control-wrapper">

              <!-- catalog button -->
              <app-catalog
                v-bind:is-show-catalog="isShowCatalog"
                v-on:click="catalogClick"
              >

              </app-catalog>
              <!-- catalog button -->

              <!-- search block -->
              <div class="search">
                <div class="search-wrapper">
                <input class="search-wrapper_input" type="text" />
                </div>
                <div class="search-btn">
                <button></button>
                </div>
              </div>
              <!-- search block -->

            </div>

            <!-- cart button -->
            <a href="#" id="cart" v-on:click="cartClick">
              <span class="counter">0</span>
              <span class="icon"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path fill="currentColor" fill-rule="nonzero"
                  d="M6 6a4 4 0 0 1 4-4h4a4 4 0 0 1 4 4v2h5.133L21.82 18.496A4 4 0 0 1 17.85 22H6.149a4 4 0 0 1-3.969-3.504L.867 8H6V6zm6 2a1 1 0 0 1 0 2H3.133l1.03 8.248A2 2 0 0 0 6.149 20h11.704a2 2 0 0 0 1.984-1.752L20.867 10H16V6a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v2h4z">
                </path>
                </svg></span>
              <span class="desc">Корзина</span>
            </a>
            <!-- cart button -->

          </div>
          </div>
        </div>
        </div>
      </nav>

      <app-cart
        v-bind:is-show-cart="isShowCart"
        v-on:close-cart="closeCart"
      ></app-cart>

      </header>
</template>

<script>
import AppCart from './AppCart.vue'
import AppCatalog from './AppCatalog.vue'

export default {
  data () {
    return {
      isShowCart: 'none',
      isShowCatalog: 'none'
    }
  },
  methods: {
    cartClick () {
      if (this.isShowCart === 'none') {
        this.isShowCart = 'flex'
      } else {
        this.isShowCart = 'none'
      }
    },
    closeCart (value) {
      this.isShowCart = value
    },

    catalogClick () {
      if (this.isShowCatalog === 'none') {
        this.isShowCatalog = 'flex'
      } else {
        this.isShowCatalog = 'none'
      }
    }

  },

  components: { AppCart, AppCatalog }

}
</script>
