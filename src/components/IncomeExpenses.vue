<script setup>
import {defineProps} from 'vue'
defineProps(['totalIncome','totalExpense'])
</script>
<template>
    <div class="w-full shadow-md h-16 border text-black flex justify-around items-center mt-4 font-bold bg-white">
        <div class="border-r-2 w-1/2 flex flex-col items-center">
            <h3 class="font-bold text-[12px]">INCOME</h3>
            <p class="text-green-600">$+{{totalIncome}}</p>
        </div>
        <div class="w-1/2 flex flex-col items-center">
            <h3 class="font-bold text-[12px]">EXPENSE</h3>
            <p class="text-red-600">${{totalExpense}}</p>
        </div>

    </div>
</template>