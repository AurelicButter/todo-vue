<template>
  <div class="main-container">
    <div class="todo-list">
      <h2>My List</h2>
      <div class="item" v-for='(item, index) in items' :key="index">
        <span class="item-title"><b>{{item.title}}</b></span>
        <span class="item-desc">{{item.desc}}</span>
        <span class="delete"><button @click='deleteItem(index)'>X</button></span>
      </div>
      <div class="item" v-if="items.length === 0">
        <p>Sorry, there is nothing to do!</p>
      </div>
    </div>

    <br />
    <div class="add-item">
      <h3>Add a new task</h3>
      <span class="input_label"><b>Title</b></span
      ><input v-model="item_title" type="text" class="title_input" />
      <br />
      <span class="input_label"><b>Description</b></span
      ><input v-model="item_desc" type="text" class="desc_input" />
      <br />
      <br />
      <span class="add_button"><button @click="add()">Add Item</button></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoPage",
  data() {
    return {
      items: [],
      item_title: "",
      item_desc: "",
    };
  },
  methods: {
    add() {
      this.items.push({ title: this.item_title, desc: this.item_desc });
      this.item_title = "";
      this.item_desc = "";
      return;
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      return;
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main-container {
  width: 300px;
  margin-left: 40%;
}

.item-title {
  margin-left: 5%;
  margin-right: 10px;
}

.add-item {
  width: 300px;
}

.add-item p {
  text-align: left;
}

.item-desc {
  margin-right: 10px;
}

.title_input {
  margin-left: 56px;
}

.input_label {
  margin-right: 5px;
}
</style>
