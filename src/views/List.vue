<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/Lego_logo_PNG2.png">
    <KitList
      msg="All Kits In Our Collection"
      v-bind:list="$options.legoJson"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import KitList from '@/components/KitList.vue'
import legoKits from '../data/lego-kits.json'

export default {
  name: 'List',
  legoJson: legoKits, // Better performance by statically storing the value here.
  components: {
    KitList
  }
}
</script>
