<template>
  <div class="wrapper">
    <AddForm @createItem="createItem" />
    <List @edit="edit" @remove="remove" :items="items" />
    <EditItemModal @edit="show" :class="{none: !showModal}" />
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
        { id: 1, title: "Evan You", desc: "Evan You is creator of Vue and vite js." },
        { id: 2, title: "Vue.js", desc: "JavaScript framework" },
        { id: 3, title: "Supabase", desc: "Alternative of Firebase." },
      ],
      showModal: false,
    }
  },
  methods: {
    remove(id) {
      this.items = this.items.filter(c => c.id !== id);
    },
    createItem(item) {
      const { title, desc } = item;
      if (title) if (desc) if (isNaN(title)) this.items.push(item);
    },
    edit(id) {
      this.showModal = id
    },
    show({target}) {
      const editItem = this.items.map(item => {
        if (item.id === this.showModal) item.title = target.value;
        return item;
      })
      this.items = editItem;
      this.showModal = false
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
  display: none;
}
</style>