<template>
  <div>
    <input type="checkbox" class="todo-item-btn"

      v-model="todo.isDone"
      
      v-on:click="changeStatus">
    <input 
      v-bind:class="{'done-item': todo.isDone, 'item-input': true}" 
      v-model="todo.value">
    <input type="button" value="X" class="rm-btn" 
      v-on:click="removeTodo">
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    changeStatus: function () {
      if (this.todo.isDone != true) {
        this.todo.isDone = true
      } else {
        this.todo.isDone = false
      }
      console.log("change 1 times")
    },
    removeTodo: function () {
      // console.log(this.i)
      // remove the element from the DOM
      this.$el.parentNode.removeChild(this.$el);
    }
  },
}
</script>

<style scoped>
.done-item {
  text-decoration:line-through;
}

.item-input {
  border:none;
  width:150px;
}

.rm-btn {
  border-radius:8px;
  border:none;
  background-color:#faa;
}
</style>