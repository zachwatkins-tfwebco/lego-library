<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Check out the lego kits we've finished!
    </p>
    <form id="lego_kit_search_form" @submit="onSubmit">
      <input name="search" id="search" type="search" list="lego-kit-data" /> <input type="submit" value="Search our Lego kits" v-on:click="onSubmit" />
      <div id="results"></div>
      <datalist id="lego-kit-data">
        <option v-for="item in items" :key="item.id" v-bind:value="item.id" />
        <option v-for="item in items" :key="item.name" v-bind:value="item.name" />
      </datalist>
    </form>
    <h3>All Kits</h3>
    <ul id="kit-list">
      <li v-for="item in items" :key="item.id" v-bind:id="'kit_' + item.id" v-bind:data-name="item.name"><span class="mono">#{{ item.id }}</span> {{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
import legoKits from '../data/lego-kits.json'

function searchKits (event) {
  event.preventDefault()
  const form = document.querySelector('#lego_kit_search_form')
  const value = form.querySelector('#search').value.trim()
  let kits = document.querySelectorAll('#kit_' + value)
  if (parseInt(value).toString() !== value) {
    // It might be that they typed in part or all of the kit name.
    kits = document.querySelectorAll('li[data-name*="' + value + '"]')
  }
  document.querySelector('#results').innerHTML = ''
  kits.forEach(element => {
    var el = document.createElement('div')
    el.innerHTML = element.innerHTML
    document.querySelector('#results').appendChild(el)
  })
}
export default {
  name: 'Kits',
  props: {
    msg: String
  },
  data () {
    return {
      items: legoKits
    }
  },
  methods: {
    onSubmit: function (event) {
      searchKits(event)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#results {
  margin: 10px 0;
  color: #00AA00;
}
h3 {
  margin: 20px 0 0;
}
#kit-list {
  max-width: 400px;
  margin: 10px auto;
}
ul {
  text-align: left;
}
a {
  color: #42b983;
}
.mono {
  font-family: monospace;
  font-size: 16px;
  font-weight: bold;
}
</style>
