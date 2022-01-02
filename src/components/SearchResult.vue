<template>
  <li>
    <span class="result-id mono">#{{ result.id }}</span>
    <span class="result-name">{{ result.name }}</span>
  </li>
</template>

<script>
export default {
  props: {
    result: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.result-id {
  display: inline-block;
  padding-right: 1em;
  font-family: monospace;
  font-size: 16px;
  font-weight: bold;
}
</style>
