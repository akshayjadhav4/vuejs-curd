<template>
  <li class="d-flex align-items-center list-group-item">
    <button
      v-if="!isEditing"
      :class="{completed}"
      @click="$emit('on-toggle')"
      class="btn border-0 text-left flex-grow-1"
    >{{todoString}}</button>
    <form v-else @submit.prevent="endEditing()" action class="flex-grow-1">
      <input @blur="startEditing()" v-model="editString" type="text" class="form-control" />
    </form>
    <button @click="startEditing()" class="btn btn-outline-primary">Edit</button>
    <button @click="$emit('on-delete')" class="btn btn-outline-danger">Delete</button>
  </li>
</template>

<script>
export default {
  props: {
    todoString: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      editString: "",
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.editString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      this.isEditing = false;
      this.$emit("on-edit", this.editString);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>