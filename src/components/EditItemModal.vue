<template>
  <div class="modal" @click="$emit('')">
    <div class="modal-main">
      <div class="modal-close"></div>
      <div class="input-group">
        <input type="text" placeholder="Title..." :value="title" @input="title = $event.target.value">
        <input placeholder="Description..." :value="desc" @input="desc = $event.target.value">
        <button @click="updateItemHandler" type="button">Edit</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "",
      desc: "",
    }
  },
  methods: {
    updateItemHandler() {
      const updateItem = {
        title: this.title,
        desc: this.desc,
      }
      this.$emit('updateItemHandler', updateItem);
      this.title = "";
      this.desc = "";
    }
  },
}
</script>
<style lang="css" scoped>
.modal {
  background-color: rgba(0, 0, 0, 0.65);
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding-top: 13px;
}

.modal-close {
  width: 30px;
  height: 30px;
  margin-bottom: 7px;
  margin-left: auto;
  cursor: pointer;
  background-color: #41b883;
  /* position: absolute;
    top: 15px; */
}

.modal-main {
  width: 650px;
  padding: 0 30px;
}

.input-group {
  display: flex;
  align-items: safe;
  justify-content: space-between;
}

input:nth-child(1) {
  width: 35%;
}

input:nth-child(2) {
  width: 55%;
  margin: 0 5px;
}

button,
input {
  padding: 10px 15px;
  outline: none;
  border: 1px solid #41b883;
  border-radius: 5px;
  display: inline-block;
  font-size: 14px;
}

button {
  font-weight: 550;
  width: 70px;
  background-color: #41b883;
  cursor: pointer;
  transition: all 0.1s;
  color: white;
}

button:hover {
  background-color: #2a8b5f;
}
</style>