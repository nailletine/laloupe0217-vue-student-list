<script>
export default {
  data() {
    return {
      firstname: '',
    };
  },
  computed: {
    addNewStudent() {
      return {
        firstname: this.firstname,
      };
    },
  },
  methods: {
    addOne() {
      this.$emit('addOne', this.addNewStudent);
    },
  },

};

</script>

<template>
  <div class="">
    <input v-model="firstname">
    <button v-on:click="addOne()">ADD</button>
  </div>
</template>

<style>

</style>
