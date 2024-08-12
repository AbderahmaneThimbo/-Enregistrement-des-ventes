<template>
  <div class="mb-3">
    <label for="designation" class="form-label">Désignation</label>
    <input
      type="text"
      id="designation"
      class="form-control"
      v-model="designation"
      @input="validate"
    />
    <div v-if="error" class="text-danger">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const designation = ref('');
const error = ref('');

const validate = () => {
  error.value = designation.value ? '' : 'La désignation est requise.';
};

defineExpose({
  designation,
  error,
  validate
});
</script>
