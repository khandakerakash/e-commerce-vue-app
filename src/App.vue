<template>
  <div id="app">
    <router-view></router-view>
    <!--<Navbar @search="search"/>-->
    <!--<div class="container">-->
      <!--<div class="row">-->
        <!--<div class="col-md-9">-->
          <!--<Inventory @addNewItem="addCartItems" :items="items"/>-->
        <!--</div>-->
        <!--<div class="col-md-3 cart-content">-->
          <!--<Cart @itemRemove="removeItem" :items="cart"/>-->
        <!--</div>-->
      <!--</div>-->
    <!--</div>-->
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Inventory from './components/Inventory.vue'
import Cart from './components/Cart.vue'
import data from './data'

export default {
  components: {
    Navbar,
    Inventory,
    Cart
  },
  data() {
    return {
      items: [],
      cart: []
    }
  },
  mounted() {
    this.items = data
  },
  methods: {
    search(keyword) {
      this.items = data.filter(item => {
         return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
      })
    },
    addCartItems(item) {
      this.cart.push(item)
    },
    removeItem(index) {
      this.cart.splice(index, 1)
    }
  }
}
</script>

<style>
  .cart-content {
    padding-top: 2%;
  }
</style>
