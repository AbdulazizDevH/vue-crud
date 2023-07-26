<template>
  <li class="list-item">
    <span :title="item.desc">{{ item.title }}</span>
    <span @click="$emit('remove', item.id)" title="Remove">Delete</span>
    <span @click="$emit('edit', item.id)" title="Rename">Edit</span>
  </li>
</template>
<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    }
  }
}
</script>
<style lang="css" scoped>
  .list-item {
    padding: 10px 20px;
    border-bottom: 1px solid #41b883;
    transition: 0.1s linear;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .list-item:last-child {
    border: none;
  }
  .list-item span:first-child {
    display: inline-block;
    width: 50%;
    padding: 10px 0;
    cursor: pointer;
  }
  span:first-child:hover {
    color: #41b883;
  }
  span:nth-child(2) {
    color: rgb(236, 110, 110);
    cursor: pointer;
  }
  span:last-child {
    cursor: pointer;
    color: cornflowerblue;
  }
  span:last-child:hover {
    color: rgb(24, 67, 146);
  }
  span:nth-child(2):hover {
    color: rgb(207, 0, 0);
  }
</style>