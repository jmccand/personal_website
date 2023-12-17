<template>
  <NuxtLink :to="props.to" target="_blank" class="border-2 rounded-md p-2 flex flex-row items-center">
    <slot>
    </slot>
  </NuxtLink>
</template>
<script setup>
 const props = defineProps({
   to: String
 });
</script>
