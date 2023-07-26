<template>
  <ul class="list">
    <ListItem v-for="item in items" :key="item.id" :item="item" 
      @removeItemHandler="$emit('removeItemHandler', $event)"
      @editItemHandler="$emit('editItemHandler', $event)" />
  </ul>
</template>

<script>
import ListItem from './ListItem.vue';
export default {
  components: { ListItem },
  props: {
    items: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style lang="css">
.list {
  min-height: 50px;
  background-color: white;
  border-radius: 10px;
  list-style: none;
  padding: 10px 20px;
}
</style>