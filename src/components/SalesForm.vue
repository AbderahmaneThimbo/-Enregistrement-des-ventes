<template>
  <form @submit.prevent="submitSale">
    <ReferenceInput ref="referenceInput" />
    <DesignationInput ref="designationInput" />
    <QuantityInput ref="quantityInput" />
    <PriceInput ref="priceInput" />

    <button type="submit" class="btn btn-primary">Enregistrer la vente</button>
  </form>

  <SalesTable :sales="sales" />
</template>

<script setup>
import { ref } from 'vue';
import ReferenceInput from './ReferenceInput.vue';
import DesignationInput from './DesignationInput.vue';
import QuantityInput from './QuantityInput.vue';
import PriceInput from './PriceInput.vue';
import SalesTable from './SalesTable.vue';

const sales = ref([]);

const submitSale = () => {
  const referenceInput = ref('referenceInput').value;
  const designationInput = ref('designationInput').value;
  const quantityInput = ref('quantityInput').value;
  const priceInput = ref('priceInput').value;

  referenceInput.validate();
  designationInput.validate();
  quantityInput.validate();
  priceInput.validate();

  if (!referenceInput.error && !designationInput.error && !quantityInput.error && !priceInput.error) {
    sales.value.push({
      reference: referenceInput.reference,
      designation: designationInput.designation,
      quantity: quantityInput.quantity,
      price: priceInput.price,
    });

    // Réinitialiser les champs
    referenceInput.reference = '';
    designationInput.designation = '';
    quantityInput.quantity = 0;
    priceInput.price = 0;
  }
};
</script>
