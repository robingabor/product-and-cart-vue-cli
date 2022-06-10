<!-- MAIN COMPONENT -->
<template>
  <header class="top-bar spread">
        <!-- Navbar -->
        <nav class="top-bar-nav">
          <router-link to="/" class="top-bar-link">
            <i class="icofont-spoon-and-fork"></i>
            <span>Home</span>
          </router-link>
          <router-link to="/products" class="top-bar-link">
            <span>Products</span>
          </router-link>
          <router-link to="/past-orders" class="top-bar-link">
            <span>Past Orders</span>
          </router-link>
        </nav>
        <!-- Cart -->
        <div @click="toggleSidebar" class="top-bar-cart-link">
          <i class="icofont-cart-alt icofont-1x"></i>
          <span>Cart ({{ totalQuantity }})</span>
        </div>
  </header>
  <!-- Router-link is sub of <a> it is added by vue router package : SPA (JS handling the routing instead of separatae HTML pages)-->
  <!-- SPA : Just showing and hiding different elements on the DOM , that is why no refreshign -->
  <!-- router-view is actually our page content -->
  <!-- the router will handle replacing this router view tag with whatever component we tell it to -->
  <!-- router view is a temporary placeholder for whatever we put on the page -->
  <router-view :inventory="inventory" :addToCart="addToCart" />

  <SidebarComp
    v-if="showSidebar"
    :toggle="toggleSidebar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
  />
</template>

<script>
import SidebarComp from '@/components/SidebarComp.vue'
import food from '@/food.json'

// this wholw object is called Options Object
// Every JS method or object will be set in here
// In VUE CLI we have one options object per component
// each component only know of their components methods and objects
export default {
  // SidebarComp must be registered
  components: {
    SidebarComp
  },
  data () {
    return {
      showSidebar: false,
      inventory: food,
      cart: {}
    }
  },
  // computed watches the changes in  variables and we will update the result every single time
  // computed then uses getters and setters
  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    }
  },
  methods: {
    addToCart (name, quantity) {
      // recieve name and number
      if (!this.cart[name]) {
        this.cart[name] = 0
      }
      this.cart[name] += quantity
      // set the input value to 0 after it is on the cart
      quantity = 0
      console.log(this.cart)
    },
    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },
    removeItem (name) {
      delete this.cart[name]
    }
  }
}
</script>
