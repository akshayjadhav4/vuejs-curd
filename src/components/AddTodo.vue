<template>
  <form @submit.prevent="addTodo()" class="col-12 col-lg-12">
    <input v-model="newTodo" placeholder="Add TODO" type="text" class="form-control" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 1) {
        this.$emit("on-addTodo", this.newTodo);
      }
      this.newTodo = "";
    },
  },
};
</script>

<style scoped>
</style>