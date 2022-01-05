<template>
  <div>
    <form id="lego_kit_search_form" v-on:submit.prevent="searchKits">
      <div class="message-wrap">
        <div id="message" v-if="newSearchTerms && 0 === results.length">
          Kit not found in our library
        </div>
        <BaseInputText
          v-model="newSearchTerms"
          id="search"
          placeholder="76146"
          list="lego-kit-data"
          v-on:input="searchKits"
        />
        <datalist id="lego-kit-data" v-if="$options.legoJson.length">
          <option v-for="kit in $options.legoJson" :key="kit.id" v-bind:value="kit.id" />
          <option v-for="kit in $options.legoJson" :key="kit.name" v-bind:value="kit.name" />
        </datalist>
        <BaseInputSubmit
          value="Search"
          v-on:click.prevent="searchKits"
        />
      </div>
    </form>
    <ul id="results" v-if="results.length">
      <KitListing
        v-for="result in results"
        :key="result.id"
        :listing="result"
      />
    </ul>
  </div>
</template>

<script>
import legoKits from '../data/lego-kits.json'
import BaseInputText from './BaseInputText.vue'
import BaseInputSubmit from './BaseInputSubmit.vue'
import KitListing from './KitListing.vue'

export default {
  legoJson: legoKits,
  components: {
    BaseInputText,
    BaseInputSubmit,
    KitListing
  },
  data () {
    return {
      newSearchTerms: '',
      results: [],
      kits: legoKits
    }
  },
  methods: {
    searchKits (value) {
      const trimmedText = this.newSearchTerms.trim()
      if (trimmedText) {
        const value = trimmedText.trim()
        const key = parseInt(value).toString() === value ? 'id' : 'name'
        // Find which kits are being looked for.
        // Replace the viewed results array with the found results.
        this.results = this.$options.legoJson.filter(function (item) {
          let searchedValue = item[key]
          if (typeof item[key] === 'number') {
            searchedValue = searchedValue.toString()
          }
          if (searchedValue.indexOf(value) >= 0) {
            return true
          } else {
            return false
          }
        })
      } else {
        this.results = []
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
#results {
  margin: 10px 0;
  max-width: 400px;
  margin: 10px auto;
  border: 1px solid #000;
  padding: 10px;
  text-align: left;
}
.message-wrap {
  display: inline-block;
  position: relative;

  #message {
    position: absolute;
    bottom: 100%;
    left: 0;
    width: 100%;
    text-align: center;
    padding: 12px;
    box-sizing: border-box;
    background: rgba(0, 0, 0, 0.85);
    border: 2px solid #FFF;
  }
}
</style>
