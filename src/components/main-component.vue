<template>
  <div :style="computedStyles" class="hello">{{ msg }}</div>
</template>

<script>

export default {
  name: "MainComponent",
  props: {
    msg: String,
    styles: Object
  },
  computed: {
    computedStyles() {
      return this.styles;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
