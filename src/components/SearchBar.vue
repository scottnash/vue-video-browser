<template>
    <div class="text-center">
       <input type="text" @input="onInput" />
    </div>
</template>

<script>
  export default {
    name: 'SearchBar',
    methods: {
      onInput(e) {
        this.$emit("termChange", e.target.value);
      }
    }
  }
</script>

<style scoped>
    input {
      width: 75%;
    }
    div {
      margin: 20px 0;
    }
</style>