<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Search our Lego kits by ID or name.<br />Press Enter to submit your search.
    </p>
    <SearchForm />
  </div>
</template>
<script>
// import Vue from 'vue'
import legoKits from '../data/lego-kits.json'
import SearchForm from './SearchForm.vue'

function searchKits (event) {
  event.preventDefault()
  const $form = document.querySelector('#lego_kit_search_form')
  // const $results = document.querySelector('#results')
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
  // Build the search results output.
  // $results.innerHTML = ''
  // if (results.length > 0) {
  //   const plural = results.length > 1 ? 's' : ''
  //   const headline = 'Found ' + results.length + ' result' + plural + ':<br />'
  //   $results.innerHTML += headline
  // }
  // console.log(results)
  // results.items = results
}
export default {
  components: {
    SearchForm
  },
  name: 'Search',
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
  max-width: 400px;
  margin: 10px auto;
  border: 1px solid #000;
  padding: 10px;
  text-align: left;
}
h3 {
  margin: 20px 0 0;
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
</style>
