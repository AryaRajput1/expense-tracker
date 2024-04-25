<script setup>
import Balance from './Balance.vue';
import {defineProps} from 'vue'
import IncomeExpenses from './IncomeExpenses.vue';
defineProps(['totalIncome','totalExpense','totalAmount'])
</script>
<template>
  <p class="font-semibold text-xl mt-8">Expense Tracker</p>
  <div>
    <Balance :totalAmount="totalAmount"/>
    <IncomeExpenses
    :totalIncome="totalIncome"
    :totalExpense="totalExpense"
    />
  </div>
</template>
