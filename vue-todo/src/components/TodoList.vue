<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
        <i class="checkBtn fa fa-check" :class="{'checkBtnCompleted' : todoItem.completed}" @click="toggleComplete(todoItem, index)"></i>
        <span :class="{'textCompleted' : todoItem.completed}">{{ todoItem.item }}</span>
        <span class="removeBtn" @click="removeTodo(todoItem, index)">
          <i class="fa fa-trash-alt"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: [ 'propsdata' ],
  methods: {
    removeTodo: function(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },

    toggleComplete: function(todoItem, index){
      todoItem.completed = !todoItem.completed;
      localStorage.removeItem(todoItem.item)
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  },
}
</script>

<style lang="scss" scoped>
ul {
  list-style-type: none;
  margin-top: 0;
  padding-left: 0;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  border-radius: 5px;
  background-color: #fff;
  line-height: 50px;
}

.checkBtn {
  margin-right: 5px;
  color: #62acde;
  line-height: 45px;
}

.checkBtnCompleted {
  color: #b3adad;
}

.textCompleted {
  color: #b3adad;
  text-decoration: line-through;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>