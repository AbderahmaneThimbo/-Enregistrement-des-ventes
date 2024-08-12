<template>
  <div class="mb-3">
    <label for="price" class="form-label">Prix</label>
    <input
      type="number"
      id="price"
      class="form-control"
      v-model.number="price"
      @input="validate"
    />
    <div v-if="error" class="text-danger">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const price = ref(0);
const error = ref('');

const validate = () => {
  error.value = price.value > 0 ? '' : 'Le prix doit être supérieur à 0.';
};

defineExpose({
  price,
  error,
  validate
});
</script>
