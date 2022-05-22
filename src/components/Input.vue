<template>
  <div id="input-container">
    <label :for="id || name">{{ label }}</label>
    <div v-if="type === 'checkbox'" id="checkboxes-container">
      <div v-for="(option, index) in options" v-bind:key="index" class="checkbox-container">
        <input :type="type" :name="name" :v-model="model" :value="option.value" />
        <span>{{ option.label }}</span>
      </div>
    </div>

    <div v-else-if="type === 'select'">
      <select :id="id" :name="name || id" :v-model="model">
        <option value="">{{ placeholder }}</option>
        <option v-for="(option, index) in options" v-bind:key="index" :value="option.value">{{ option.label }}</option>
      </select>
    </div>

    <div v-else="type === 'text'">
      <input :type="type" :id="id" :name="name || id" :v-model="model" :value="value" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Input",
  props: ["label", "id", "type", "name", "model", "value", "placeholder", "options"]
}
</script>

<style scoped>
#input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#checkboxes-container {
  display: flex;
  flex-wrap: wrap;
}

.checkbox-container {
  display: flex;
  align-items: center;
  width: 50%;
  margin-bottom: 20px;
  gap: 6px;
}

.checkbox-container input,
.checkbox-container span {
  width: auto;
  font-weight: bold;
}
</style>
