<template>
  <div class="field">
    <label class="label">Email</label>
    <div class="control">
      <input
        :value="props.value"
        @input="props.handleInput"
        class="input"
        :name="props.name"
        :class="{
          'is-danger': true,
          'is-success': false,
        }"
        :type="props.type"
      />
    </div>
    <p class="help is-danger">{{ errorMessage }}</p>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  handleInput: {
    type: Function,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
  type: {
    type: string,
    required: false,
    default: "text",
  },
});
</script>

<style scoped></style>
