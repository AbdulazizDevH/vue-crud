<template>
  <div>
    <input @change="edit" type="text">
  </div>
</template>
<script>
export default {
  methods: {
    edit(e) {
      this.$emit('edit', e);
      e.target.value = ""
    }
  },
}
</script>
<style lang="">
  
</style>