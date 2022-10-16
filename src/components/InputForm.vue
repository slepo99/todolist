<template>
  <div class="header">
    <h2>My To Do List</h2>
    <input placeholder="Add new task" @input="addTask" :value="modelValue" />
    <button @click.enter="pushTask" class="addBtn">add</button>
  </div>
</template>

<script>
export default {
  name: "input-form",
  props: {
    modelValue: [String, Number],
  },

  methods: {
    addTask(event) {
      return this.$emit("update:modelValue", event.target.value);
    },
    pushTask() {
      return this.$emit("pushTask");
    },
  },
};
</script>

<style scoped>
input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 16px;
  outline: none;
}

.addBtn {
  padding: 10px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
  border: none;
}
.addBtn:hover {
  background-color: #bbb;
}
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;
}
.header:after {
  content: "";
  display: table;
  clear: both;
}
</style>
