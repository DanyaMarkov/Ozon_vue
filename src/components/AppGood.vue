<template>

        <div class="col-12 col-md-6 col-lg-4 col-xl-3" v-for="good in goods" :key="good.id" >
          <div class="card">
            <div class="card-sale" v-if="good.sale == true">🔥Hot Sale🔥</div>
            <div class="card-img-wrapper">
              <span class="card-img-top"
                :style="{backgroundImage: `url(${good.img})`}"></span>
            </div>
            <div class="card-body justify-content-between">
              <div class="card-price">{{good.price}}</div>
              <h5 class="card-title">{{good.title}}</h5>
              <button class="btn btn-primary">В корзину</button>
            </div>
          </div>
        </div>

</template>

<script>
export default {
  props: ['goods']

}
</script>
