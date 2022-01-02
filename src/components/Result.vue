<template>
  <div class="result">
    <span class="item-id">{{ id }}</span>
    <span class="item-name">{{ name }}</span>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: {
    id: String,
    name: String
  },
  render: function (createElement) {
    return createElement(
      'div',
      
    )
  }
}
</script>
