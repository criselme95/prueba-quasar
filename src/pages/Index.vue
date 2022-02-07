<template>
  <div class="q-pa-md">
    <q-carousel
      animated
      v-model="slide"
      arrows
      navigation
      infinite
      height="400px"
    >
      <q-carousel-slide :name="1" img-src="https://catalogo.claro.com.ec/banner-tienda.jpg" />
      <q-carousel-slide :name="2" img-src="https://static-or01.inbenta.com/50e033c7c158c1f2ced45ea4f046c55e0efa637298e3127904afb4551be3627a/PlanSolidario/2020/abril/img/banner.jpg" />
      <q-carousel-slide :name="3" img-src="https://www.neufsa.com/assets/claro%203.jpg" />
      
    </q-carousel>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      slide: ref(1)
    }
  }
}
</script>