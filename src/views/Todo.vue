<template>
  <div id="todo" class="center-div">
    <div id="header" class="left-div">
      <h2>To-Do List</h2>
      <div>
        新增：
        <input type="text" id="text" v-model="input_value"
          v-on:keypress="keyNew">
        <input type="submit" value="新增" id="submit"
          v-on:click="newToDo">
        <input type="button" value="清除" id="clear">
      </div>
    </div>

    <div>
      <div id="todo" class="list">
        <p>TO-DO</p>
        <div class="left-div">
          <div class="li-div">
            <TodoItem
              v-for="todo_list in todo_lists"
              :key="todo_list.index"
              v-bind:todo="todo_list"
            >
            </TodoItem>
          </div>
        </div>
      </div>

      <div id="done" class="list">
        <p>DONE</p>
        <div class="left-div">
          <div class="li-div">
            <TodoItem
              v-for="done_list in done_lists"
              :key="done_list.index"
              v-bind:todo="done_list"
            >
            </TodoItem>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'

export default {
  name: 'Todo',
  data() {
    return {
      input_value: "",
      lists: [
        { isDone: false, value: "公文送係辦" },
        { isDone: true, value: "git作業" }
      ]
    }
  },
  computed: {
    todo_lists () {
      return this.lists.filter(list => !list.isDone)
    },
    done_lists () {
      return this.lists.filter(list => list.isDone)
    }
  },
  methods: {
    newToDo: function () {
      this.lists.push({ isDone: false, value: this.input_value })

      this.input_value = ""
    },
    keyNew: function (e) {
      if(e.keyCode === 13) {
        this.newToDo();
      }
    }

  },
  components: {
    TodoItem,
  }
}
</script>

<style scoped>
.center-div {
  text-align:center;
}

#header {
  width:500px;
  display:inline-block;
}

.left-div {
  text-align:left;
}

.list {
  display:inline-block;
  width:200px;
  margin-top:20px;
  margin-right:20px;
  padding:10px 10px;
  border:solid;
  
  vertical-align:top; /*對齊頂端*/
}
</style>