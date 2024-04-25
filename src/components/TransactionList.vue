
<script setup>
import TransactionCard from './TransactionCard.vue';
import {defineProps} from 'vue';

defineProps(['list'])

</script>
<template>
    <div class="w-full mt-4">
        <div class="w-full border-b-2 font-bold py-2 border-gray-300">
            <h3>History</h3>
        </div>
        <template v-if="list?.length">
        <TransactionCard v-for="item in list" :key="item.id" :listItem="item" @on-delete="id=>$emit('onDelete',id)"/>
        </template>
            <h3 v-else class="mt-2 text-sm text-gray-400">No transaction history</h3>
    </div>
</template>