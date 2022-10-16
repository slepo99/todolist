<template>
  <div>
    <InputForm v-model="text" @pushTask="pushTask" />

    <ul v-for="(task, id) in tasks" :key="task.id">
      <li
        :class="{ checked: task.isActive }"
        @click="task.isActive = !task.isActive"
      >
        {{ id + 1 }}. &nbsp;
        {{ task.title }}
      </li>
      <span class="close" @click="removeTodo(id)">&#215;</span>
    </ul>
  </div>
</template>

<script>
import InputForm from "./InputForm.vue";

export default {
  name: "task-list",
  components: { InputForm },
  data() {
    return {
      text: "",
      tasks: [],
    };
  },
  methods: {
    pushTask() {
      const newTask = {
        title: this.text,
        id: Date.now(),
        isActive: false,
      };
      if (this.text.length > 0) {
        this.tasks.push(newTask);
      }
      this.text = "";
    },

    removeTodo(id) {
      return this.tasks.splice(id, 1);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
ul {
  margin: 5px 0;
  padding: 0;
  display: flex;
}
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  width: 95%;
}
ul li:nth-child(odd) {
  background: #f9f9f9;
}
ul li:hover {
  background: #f44336;
}
ul li.checked {
  background: #888;
  color: #fff;
  text-decoration: line-through;
}
ul li.checked::before {
  content: "";
  position: absolute;
  border-color: #fff;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 10px;
  left: 16px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}
.close {
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
  width: 5%;
  background: #f9f9f9;
}

.close:hover {
  background-color: #f44336;
  color: white;
}
</style>
