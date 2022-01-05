<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul id="kit-list">
      <li v-for="item in items" :key="item.id" v-bind:id="'kit_' + item.id" v-bind:data-name="item.name"><span class="mono kit-id">#{{ item.id }}</span> <span class="kit-name">{{ item.name }}</span></li>
    </ul>
  </div>
</template>

<script>
import legoKits from '../data/lego-kits.json'

export default {
  name: 'KitList',
  props: {
    msg: String
  },
  data () {
    return {
      items: legoKits
    }
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
