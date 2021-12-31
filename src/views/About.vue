<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/logo.png">
    <Kits msg="Lego Kit Library" />
  </div>
</template>

<script>
// @ is an alias to /src
import Kits from '@/components/Kits.vue'

export default {
  name: 'About',
  components: {
    Kits
  }
}
</script>
