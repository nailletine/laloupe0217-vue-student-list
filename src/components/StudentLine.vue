<script>
  export default {
    props: ['student', 'indexA'],
    data() {
      return {
        editInput: '',
      };
    },
    computed: {
      editNewStudent() {
        return {
          firstname: this.editInput,
        };
      },
    },
    methods: {
      removeStudent() {
        this.$emit('remove');
      },
      editStudent() {
        this.$emit('edit', this.editNewStudent, this.indexA);
        this.editInput = '';
      },
    },
  };
</script>

<template>
  <div>
      {{student.firstname}}
    <button v-on:click='removeStudent()'>Delete</button>
  <button v-on:click='editStudent()'>Edit</button> <input v-model="editInput">
  </div>
</template>
<style>
</style>
