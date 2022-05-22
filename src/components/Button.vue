<template>
  <button :type="type">{{ label }}</button>
</template>

<script lang="ts">
export default {
  name: "Button",
  props: ["type", "label"]
}
</script>

<style scoped>
button {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  transition: .5s;
}

button:hover {
  background-color: transparent;
  color: #222;
}
</style>
