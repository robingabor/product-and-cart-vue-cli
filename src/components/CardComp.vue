<template>
    <div >
        <div class="card-title">
            <!-- item name -->
            {{ item.name }}
        </div>
        <div class="card-body">
            <!-- item icon -->
            <i :class="iconClass + item.icon"></i>
            <form>
                <div class="row">
                  <div class="cell">
                    <label>Type:</label>
                  </div>
                  <div class="cell">
                    <em>{{ item.type }}</em>
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Price:</label>
                  </div>
                  <div class="cell">
                    {{ item.price.USD }}
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Quantity:</label>
                  </div>
                  <div class="cell">
                    <input type="number" v-model.number="quantity">
                  </div>
                </div>
            </form>
        </div>
        <div class="card-footer">
            <button @click="addToCart( item.name,quantity)" class="btn btn-light">Add to cart</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'CardComp',
  props: [
    'inventory',
    'addToCart',
    'item',
    'index'
  ],
  data () {
    return {
      quantity: 0,
      iconClass: 'icofont-10x icofont-'
    }
  }
}
</script>
