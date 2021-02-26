<template>
  <div class="content">
    <div>
      <h1>ToDo List</h1>
    </div>
    <div class="add">
      <input
        type="text"
        v-model="formvalue"
        placeholder="Enter to-do"
        class="inputstyle"
      />
      <button @click="add" class="button addbutton">Add</button>
    </div>
    <div class="list">
      <ul>
        <li
          v-for="(todo, index) in todos"
          :key="index"
          :class="{ check: todo.done, checknodone: !todo.done }"
        >
          <div class="labelstyle">
            <label>{{ index + 1 }}.{{ todo.value }}</label>
            <button @click="done(index)" class="button donebutton">Done</button>
            <button @click="undone(index)" class="button undonebutton">
              Undone
            </button>
            <button @click="deleteitem(index)" class="button debutton">
              Delete
            </button>
          </div>
          <hr v-if="index + 1 != todos.length" />
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: "Todo",
  data() {
    return {
      todos: [
        { value: "test1", done: false },
        { value: "test2", done: true },
        { value: "test3", done: false },
      ],
      formvalue: "",
    };
  },
  methods: {
    add() {
      if (this.formvalue != "") {
        this.todos.push({
          value: this.formvalue,
          done: false,
        });
        this.formvalue = "";
      }
    },
    deleteitem(item) {
      this.todos.splice(item, 1);
    },
    done(item) {
      this.todos[item].done = true;
    },
    undone(item) {
      this.todos[item].done = false;
    },
  },
};
</script>
<style scoped>
h1 {
  color: #8e8e8e;
}
.content {
  padding: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.list ul {
  list-style-type: none;
  text-indent: -5px;
  padding-left: 15px;
}
.list li {
  line-height: 1.1;
  font-size: 25px;
}
.list label {
  /* margin-left: 50px; */
  white-space: pre-wrap;
  white-space: -moz-pre-wrap;
  white-space: -pre-wrap;
  white-space: -o-pre-wrap;
  word-wrap: break-word;
}
.check {
  color: #bebebe;
  text-decoration: line-through;
}
.list {
  width: 60%;
  background-color: azure;
  border-width: 1px;
  box-shadow: 5px 5px 7px #d0d0d0;
}
.labelstyle {
  margin-left: 50px;
  margin-right: 50px;
  word-wrap: break-word;
  white-space: normal;
}
.list hr {
  margin-right: 35px;
  width: 95%;
  color: #adadad;
}
.checknodone {
  color: #7b7b7b;
}
.add {
  margin-bottom: 30px;
}
.add input {
  margin-right: 5px;
}
.button {
  border: none;
  border-radius: 4px;
  color: white;
  padding: 6px 12px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
}
.debutton {
  background-color: #ff7575;
  margin-left: 5px;
}
.donebutton {
  background-color: #97cbff;
  margin-left: 60px;
}
.undonebutton {
  background-color: #c7c7e2;
  margin-left: 5px;
}
.addbutton {
  background-color: #a3d1d1;
  font-size: 14px;
}
.inputstyle {
  outline-style: none;
  border: 0px;
  border-radius: 3px;
  padding: 6px 0px;
  width: 200px;
}
</style>
