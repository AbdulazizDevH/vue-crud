<template>
  <div class="wrapper">
    <AddForm @createItem="createItemHandler" />
    <List @editItemHandler="editItemHandler" @onLikeHandler="onLikeHandler" @removeItemHandler="removeItemHandler" :items="items" />
    <EditItemModal @updateItemHandler="updateItemHandler" :class="{none: !showModal}" />
  </div>
</template>

<script>
import AddForm from './components/AddForm.vue';
import List from './components/List.vue';
import EditItemModal from './components/EditItemModal.vue';
export default {
  components: {
    AddForm,
    List,
    EditItemModal
  },
  data() {
    return {
      items: [
        { id: 1, like: false, title: "Evan You", desc: "Evan You is creator of Vue and vite js." },
        { id: 2, like: false, title: "Vue.js", desc: "JavaScript framework" },
        { id: 3, like: false, title: "Supabase", desc: "Alternative of Firebase." },
      ],
      showModal: false,
      editId: "",
    }
  },
  methods: {
    onLikeHandler(id) {
      this.items = this.items.map(l => {
        if (l.id == id) l.like = !l.like;
        return l;
      })
    },
    removeItemHandler(id) {
      this.items = this.items.filter(c => c.id !== id);
    },
    createItemHandler(item) {
      const { title, desc } = item;
      if (title) if (desc) if (isNaN(title)) this.items.push(item);
    },
    updateItemHandler({title, desc}, modal) {
      if (title) {
        this.items = this.items.filter(c => {
          if (c.id == this.editId) c.title = title;
          return c;
        })
        this.showModal = false;
      }
      if (desc) {
        this.items = this.items.filter(c => {
          if (c.id == this.editId) c.desc = desc;
          return c;
        })
        this.showModal = false;
      }
    },
    editItemHandler(id) {
      this.showModal = true;
      this.editId = id;
    }
  },
}
</script>

<style lang="css">
.wrapper {
  max-width: 650px;
  padding: 0 30px;
  margin: 50px auto;
}
.none {
  display: none !important;
}
</style>