<script setup>
import Header from "./components/Header.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import {computed, onBeforeMount, onMounted, ref} from 'vue'
import { useToast } from "vue-toastification";

const totalIncome = computed(()=>{
  return list.value?.reduce((sum,item)=>{
    if(item.price<=0){
      return sum
    }
    return sum+item.price
  },0) || 0
})
const totalExpense = computed(()=>{
  return list.value?.reduce((sum,item)=>{
    if(item.price>=0){
      return sum
    }
    return sum+item.price
  },0) || 0
})
const totalAmount = computed(()=>{
  return totalIncome.value + totalExpense.value
})
const toast = useToast()
const list = ref([])

onBeforeMount(()=>{
  const savedlist = JSON.parse(localStorage.getItem("list"));
  console.log(savedlist);
  if(savedlist){
    list.value = savedlist
    console.log(list.value); 
  }else{
  list.value = []
}
})

const onAddTransaction = (payload)=>{
  list.value = [payload,...list.value]
  toast.success('Added Successfully!')
  localStorage.setItem('list', JSON.stringify(list.value))

}

const onDelete= (payload)=>{
  console.log('delete')
  list.value = list.value.filter(item=>item.id!=payload)
  toast.success('Deleted Successfully!')
  localStorage.setItem('list', JSON.stringify(list.value))

}
</script>


<template>
  <div class="font-mono w-full flex justify-center items-center bg-gray-50">
  <div class="w-full sm:w-3/5 mx-8 mt-4 sm:m-2 h-full border px-6 bg-gray-100 shadow-xl">
    <Header :totalAmount="totalAmount"
    :totalExpense="totalExpense"
    :totalIncome="totalIncome" />
    <TransactionList @on-delete="onDelete" :list="list"/>
    <AddTransaction @on-add="onAddTransaction"/>
  </div>
</div>

</template>

<style scoped></style>
