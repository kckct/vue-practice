<template>
  <div>
    <select v-on:change="selectedChange">
      <option v-for="option in options" v-bind:value="option.name">
        {{ option.name }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: ["options", "selected"],

  methods: {
    selectedChange(event) {
      this.$emit("selected-change", event.target.value);
    }
  }
};
</script>