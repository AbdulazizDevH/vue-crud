<template>
  <div class="input-group">
    <input type="text" placeholder="Title..." :value="title" @input="title = $event.target.value">
    <textarea placeholder="Text..." :value="desc" @input="desc = $event.target.value"></textarea>
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
        id: Math.random()
      }
      this.$emit("createItem", newItem);
      this.title = "";
      this.desc = "";
    }
  },
}
</script>

<style scoped>
.input-group {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(auto, 100%));
  grid-template-rows: 1fr 1fr;
  gap: 5px;
  margin-bottom: 10px;
}
input {
  /* width: 450px; */
}
button {
  width: 120px;
  border: 1px solid #41b883;
  outline: none;
  background-color: #41b883;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.1s;
  color: white;
}
button:hover {
  background-color: #2a8b5f;
}
textarea, input {
  padding: 5px 15px;
  outline: none;
  border: 1px solid #41b883;
  border-radius: 5px;
  display: inline-block;
}
.input-group textarea {
  grid-row: 2 / 3;
  resize: none;
  grid-column: 1 / 3;
  
}
</style>