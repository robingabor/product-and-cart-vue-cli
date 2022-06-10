<template>
  <!-- Main Container -->
    <main class="wrapper">
        <h1>Products</h1>

        <div class="card-container">

          <!-- Card Component -->
          <CardComp
            v-for="(item,index) in inventory"
            :key="item.id"
            class="card"
            :item="item"
            :index="index"
            :addToCart="addToCart"
            :inventory="inventory"
          />
        </div>
    </main>
</template>

<script>
import CardComp from '@/components/CardComp.vue'
export default {
  name: 'ProductsView',
  // recieving props from App.vue
  props: [
    'inventory',
    'addToCart'
  ],
  components: { CardComp }
}
</script>
