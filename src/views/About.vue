<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/logo.png">
    <Kits msg="Lego Kit Library" />
  </div>
</template>

<script>
// @ is an alias to /src
import Kits from '@/components/Kits.vue'
// import Vue from 'vue'
// import legoKits from '../data/lego-kits.json'

/* exported kitList */
// Kits.items = [
//   { id: 76169, name: 'Thor Mech Armor' },
//   { id: 76171, name: 'Miles Morales Mech Armor' },
//   { id: 76168, name: 'Captain America Mech Armor' }
// ]

export default {
  name: 'About',
  components: {
    Kits
  }
}
</script>
