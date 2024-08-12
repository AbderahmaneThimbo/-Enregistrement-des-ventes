<template>
  <div class="mb-3">
    <label for="reference" class="form-label">Référence</label>
    <input
      type="text"
      id="reference"
      class="form-control"
      v-model="reference"
      @input="validate"
    />
    <div v-if="error" class="text-danger">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const reference = ref('');
const error = ref('');

const validate = () => {
  error.value = reference.value ? '' : 'La référence est requise.';
};

defineExpose({
  reference,
  error,
  validate
});
</script>
