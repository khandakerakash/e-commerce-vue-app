<template>
  <ul class="list-group">
    <li class="list-group-item">
      <span class="item-name">Name</span>
      <span class="item-price float-right">Price</span>
    </li>
    <hr>
    <li class="list-group-item" v-for="(item, index) in items" :key="index">
      <button class="btn btn-danger btn-sm" @click="removeItem(index)">-</button>
      <span class="item-name">{{ (index + 1) }}. {{ item.title }}</span>
      <span class="item-price float-right">${{ item.price }}</span>
    </li>
    <hr>
    <li class="list-group-item">
      <span class="item-name"><strong>Total</strong></span>
      <span class="item-price float-right"><strong>${{ totalPrice }}</strong></span>
    </li>
  </ul>
</template>

<script>
  export default {
    props: ['items'],
    computed: {
      totalPrice() {
        var total = 0
        this.items.forEach(item => {
          total += parseFloat(item.price)
        })
        return total
      }
    },
    methods: {
      removeItem(index) {
        this.$emit('itemRemove', index)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
