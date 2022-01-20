<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class="fa fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      newTodoItem : "",
    }
  },

  methods: {
    addTodo: function() {
      var obj = { completed : false, item : this.newTodoItem }
      localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
      this.clearInput();
    },

    clearInput: function(){
      this.newTodoItem = '';
    }
  },
}
</script>

<style lang="scss" scoped>
input {

  &:focus {
    outline: none;
  }
}

.inputBox {
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  background-color :#fff;

  input {
    float:left;
    width: calc(100% - 3rem);
    height: 100%;
    padding: 0 10px;
    border-style: none;
    box-sizing: border-box;
    font-size: 0.9rem;
  }
}

.addContainer {
  float: right;
  display: block;
  width: 3rem;
  background: linear-gradient(to right, #6478fb, #8763fb);
  border-radius: 0 5px 5px 0;
}

.addBtn {
  color: #fff;
  vertical-align: middle;
}
</style>