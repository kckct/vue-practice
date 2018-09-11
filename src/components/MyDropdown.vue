<template>
    <select v-on:change="selectedChange">
      <option v-for="(option, index) in options" :value="index" :key="index">
        {{ option.name }}
      </option>
    </select>
</template>

<script>
export default {
  props: ["options", "selected"],

  methods: {
    selectedChange(event) {
      this.$emit("input", event.target.value);
    }
  }
};
</script>