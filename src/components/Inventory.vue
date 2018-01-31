<template>
  <div class="row">
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <div class="card" style="width: 16rem;">
          <img class="card-img-top" :src="item.photo" :alt="item.title">
          <div class="card-body">
            <h5 class="card-title">{{ item.title }}</h5>
            <p class="card-text">{{ item.price }}</p>
            <a class="btn btn-success" @click="addTocart(item)">+ Add</a>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    props: ['items'],
    methods: {
      addTocart(item) {
        this.$emit('addNewItem', item)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  ul {
    list-style-type: none!important;
    margin: 0!important;
    padding: 0!important;
  }

  ul li {
    padding: 22px 10px 5px 10px;
    display: inline-block!important;
  }
</style>
