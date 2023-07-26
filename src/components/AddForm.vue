<template>
  <div class="input-group">
    <input type="text" placeholder="Title..." :value="title" @input="title = $event.target.value">
    <input placeholder="Description..." :value="desc" @input="desc = $event.target.value">
    <button type="button" @click="addFormHandler">Add</button>
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
    addFormHandler() {
      const newItem = {
        like: false,
        title: this.title,
        desc: this.desc,
        id: Math.floor(Math.random() * 1000),
      }
      this.$emit("createItem", newItem);
      this.title = "";
      this.desc = "";
    }
  },
}
</script>

<style lang="css" scoped>
.input-group {
  width: 100%;
  display: flex;
  align-items: safe;
  justify-content: space-between;
  margin-bottom: 10px;
}
input:nth-child(1) {
  width: 35%;
}
input:nth-child(2) {
  width: 55%;
  margin: 0 5px;
}
button, input {
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