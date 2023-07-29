<template>
  <li class="list-item" :class="{like: item.like}">
    <span @click="$emit('onLikeHandler', item.id)" :title="item.desc">{{ item.title }}</span>
    <span @click="$emit('removeItemHandler', item.id)" title="Remove">
      <i class="fa-solid fa-trash-can"></i>
    </span>
    <span @click="$emit('editItemHandler', item.id)" title="Rename">
      <i class="fa-regular fa-pen-to-square"></i>
    </span>
    <i class="vue fa-brands fa-vuejs"></i>
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
    width: 75%;
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
  span:nth-child(3) {
    cursor: pointer;
    color: cornflowerblue;
    margin-right: 10px;
  }
  span:nth-child(3):hover {
    color: rgb(24, 67, 146);
  }
  span:nth-child(2):hover {
    color: rgb(207, 0, 0);
  }
  .vue {
    color: #41b883;
    font-size: 20px;
    transform: translateX(35px);
    opacity: 0;
    transition: all 0.15s ease-in;
  }
  .list-item.like .vue {
    transform: translateX(0);
    opacity: 1;
  }
  .list-item.like span:first-child {
    color: #41b883;
  }
</style>