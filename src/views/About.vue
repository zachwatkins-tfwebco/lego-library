<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/logo.png">
    <LessonsLearned msg="Source Code and Lessons Learned"/>
  </div>
</template>

<script>
// @ is an alias to /src
import LessonsLearned from '@/components/LessonsLearned.vue'

export default {
  name: 'About',
  components: {
    LessonsLearned
  }
}
</script>
