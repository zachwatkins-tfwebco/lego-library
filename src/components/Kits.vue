<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Check out the lego kits we've finished!
    </p>
    <h3>Kits</h3>
    <ul id="kit-list">
      <li v-for="item in items" :key="item.id">#{{ item.id }}</li>
    </ul>
  </div>
</template>

<script>
import Vue from 'vue'
import legoKits from '../data/lego-kits.json'

/* exported kitList */
var kitItems = new Vue({ // eslint-disable-line no-new
  el: '#kit-list',
  data () {
    return {
      items: legoKits
    }
  }
})
export default {
  name: 'Kits',
  props: {
    msg: String,
    items: kitItems
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
