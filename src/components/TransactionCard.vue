<script setup>
import {defineProps,ref} from 'vue'
defineProps({
  listItem: 'object'
});
const shouldShowDelete = ref(false);
</script>
<template>
  <div @mouseover="shouldShowDelete=true" @mouseleave="shouldShowDelete=false" class="flex my-3 flex-row ">
    <div @click="$emit('onDelete',listItem.id)" v-if="shouldShowDelete" class="bg-red-200 w-10 flex-col flex justify-center items-center font-bold text-red-900 shadow-md pointer">x</div>
    <div
      class="pointer f-full p-3 w-full bg-white shadow-md border border-r-4"
      :class="listItem.price < 0 ? 'border-r-red-400' : 'border-r-green-400'"
    >
      <div class="flex justify-between font-bold">
        <p>{{ listItem.label }}</p>
        <p>${{ listItem.price }}</p>
      </div>
    </div>
  </div>
</template>
