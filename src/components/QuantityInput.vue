<template>
  <div class="mb-3">
    <label for="quantity" class="form-label">Quantité</label>
    <input
      type="number"
      id="quantity"
      class="form-control"
      v-model.number="quantity"
      @input="validate"
    />
    <div v-if="error" class="text-danger">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const quantity = ref(0);
const error = ref('');

const validate = () => {
  error.value = quantity.value > 0 ? '' : 'La quantité doit être supérieure à 0.';
};

defineExpose({
  quantity,
  error,
  validate
});
</script>
