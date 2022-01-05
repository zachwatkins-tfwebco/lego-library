<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul id="kit-list">
      <KitListing
        v-for="item in list"
        :key="item.id"
        :listing="item"
      />
    </ul>
  </div>
</template>

<script>
import KitListing from './KitListing.vue'

export default {
  name: 'KitList',
  props: {
    msg: String,
    list: Array
  },
  components: {
    KitListing
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#kit-list {
  max-width: 400px;
  margin: 10px auto;
  border: 1px solid #000;
  border-width: 0 1px;
  padding: 10px;
}
ul {
  display: table;
  text-align: left;
  margin-left: 0;
  padding-left: 0;
}
</style>
