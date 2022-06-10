<template>
  <div class="home">
      <!--Hero  -->
    <div class="splash-container">
        <div class="splash">
          <h1>Splendid Food</h1>
        </div>
    </div>
    <!-- main -->
    <main class="wrapper">

      <h2>Recommended</h2>

      <div class="recommended">
          <!-- Carrot Card -->
        <!-- Card Component -->
        <CardComp
          v-for="(item,index) in inventory.slice(0,3)"
          :key="item.id"
          class="card"
          :item="item"
          :index="index"
          :addToCart="addToCart"
          :inventory="inventory"
        />
      </div>

    </main>
  </div>
</template>

<script>
// importing our json wich going to be our inventory
// @ is an alias to /src
import CardComp from '@/components/CardComp.vue'

export default {
  name: 'HomeView',
  // recieving props from App.vue
  props: [
    'inventory',
    'addToCart'
  ],
  components: {
    CardComp
  }
}
</script>
