<template>
  <div type="text">
    <label class="font-mono text-gray-700 dark:text-gray-200" for="username"
      >License Plate</label
    >
    <input
      placeholder="XXX-1234"
      class="w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-200 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-black focus:ring-gray-300 focus:ring-opacity-40 dark:focus:border-gray-300 focus:outline-none focus:ring"
      :value="licensePlate"
      @change="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script setup>
/*
  Input Props
 */

const props = defineProps({
  licensePlate: {
    type: [String, Number],
    default: "",
  },
});
</script>
