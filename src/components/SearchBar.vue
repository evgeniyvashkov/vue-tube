<template>
  <div>
    <input
        placeholder="Type for search"
        @input="onInput"
    />
  </div>
</template>

<script>


export default {
  name: 'SearchBar',
  methods: {
    onInput(event) {
      this.$emit('termChange', event.target.value)
    }
  }
}
</script>

<style scoped>
div {
  margin: 20px 0;
  text-align: center;
}

input {
  width: 75%;
  padding: 5px 10px;
  box-sizing: border-box;
}
</style>