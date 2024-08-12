<template>
  <table class="table table-striped mt-4">
    <thead>
      <tr>
        <th>Référence</th>
        <th>Désignation</th>
        <th>Quantité</th>
        <th>Prix</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="sale in sales" :key="sale.reference">
        <td>{{ sale.reference }}</td>
        <td>{{ sale.designation }}</td>
        <td>{{ sale.quantity }}</td>
        <td>{{ sale.price }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  sales: Array,
});
</script>
