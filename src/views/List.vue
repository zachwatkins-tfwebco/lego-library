<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/logo.png">
    <KitList msg="All Kits In Our Collection"/>
  </div>
</template>

<script>
// @ is an alias to /src
import KitList from '@/components/KitList.vue'

export default {
  name: 'List',
  components: {
    KitList
  }
}
</script>
