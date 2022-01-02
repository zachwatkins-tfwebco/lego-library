<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Search our Lego kits by ID or name.
    </p>
    <form id="lego_kit_search_form" @submit="onSubmit">
      <input name="search" id="search" type="search" list="lego-kit-data" /> <input type="submit" value="Search Kits" v-on:click="onSubmit" />
      <div id="results"><Result /></div>
      <datalist id="lego-kit-data">
        <option v-for="item in items" :key="item.id" v-bind:value="item.id" />
        <option v-for="item in items" :key="item.name" v-bind:value="item.name" />
      </datalist>
    </form>
  </div>
</template>

<script>
// import Vue from 'vue'
import legoKits from '../data/lego-kits.json'
import Result from './Result.vue'

function searchKits (event) {
  event.preventDefault()
  const $form = document.querySelector('#lego_kit_search_form')
  const $results = document.querySelector('#results')
  const value = $form.querySelector('#search').value.trim()
  const key = parseInt(value).toString() === value ? 'id' : 'name'
  const results = []
  // Find which kits are being looked for.
  legoKits.forEach(element => {
    let searchedValue = element[key]
    if (typeof element[key] === 'number') {
      searchedValue = searchedValue.toString()
    }
    if (searchedValue.indexOf(value) >= 0) {
      results.push(element)
    }
  })
  Result.render({ el: '#results' }) // eslint-disable-line no-new
  // Build the search results output.
  $results.innerHTML = ''
  if (results.length > 0) {
    const plural = results.length > 1 ? 's' : ''
    const headline = 'Found ' + results.length + ' result' + plural + ':<br />'
    $results.innerHTML += headline
  }
  results.forEach(element => {
    // var el = document.createElement('div')
    console.log(Result)
    // el.innerHTML = element.innerHTML
    // $results.appendChild(el)
  })
}
export default {
  components: {
    Result
  },
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
  border: 1px solid #000;
  padding: 10px;
}
ul {
  text-align: left;
  margin-left: 0;
  padding-left: 0;
}
li {
  list-style-type: none;
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
