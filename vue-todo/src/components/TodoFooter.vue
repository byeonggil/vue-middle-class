<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo: function(){
      localStorage.clear();
    }
  },
}
</script>

<style lang="scss" scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  margin: 0 auto;
  border-radius: 5px;
  background-color :#fff;
  line-height: 50px;
}

.clearAllBtn {
  display: block;
  color: #e20303;
}
</style>