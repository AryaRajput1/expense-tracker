
<script setup>
import TransactionCard from './TransactionCard.vue';
import {defineEmits,ref} from 'vue'
import {useToast} from 'vue-toastification'

const toast = useToast();
const label = ref('')
const price =  ref(null)
const errorMessage = ref('Something went wrong')
const isError = ref(false)
const emit = defineEmits('onAdd')
const onAdd = ()=>{
    isError.value = false
    if(label.value && price.value){
        emit('onAdd', {
            id: Date.now(),
            label: label.value,
            price: parseFloat(price.value)
        })
        label.value =''
        price.value = null
        return ;
    }
    toast.error('Both fields must filled')
    isError.value = true
}
</script>
<template>
    <div class="w-full mt-4">
        <div class="w-full border-b-2 font-bold py-2 border-gray-300">
            <h3>Add new transaction</h3>
        </div>
        <div class="flex flex-col">
            <label class="mt-4 my-2 font-bold  text-sm">Label</label>
            <input v-model="label" placeholder="Enter label" type="text" class="border text-md outline-blue-500 p-2">
            <label class="mt-4 my-2 font-bold  text-sm">Amount (Negative-Expense Positive-Income)</label>
            <input 
            v-model="price" 
            placeholder="Enter amount" type="number" class="border text-md outline-blue-500 p-2">
            
            <button class="border bg-violet-400 p-2 text-white font-bold my-4 rounded-md" @click="onAdd"> Add Transaction</button>

        </div>
    </div>
</template>