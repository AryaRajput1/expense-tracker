<script setup>
import {defineProps} from 'vue'
defineProps(['totalAmount'])
</script>
<template>
    <div class="w-full">
        <h3 class="mt-6 font-semibold">Your Balance</h3>
        <p class="text-2xl font-bold">${{totalAmount}}</p>
    </div>
</template>