<template>
  <NuxtLink :to="props.to" target="_blank" class="items-center min-w-fit pr-4 underline" @click="(event) => event.stopPropagation()">
    <slot>
    </slot>
  </NuxtLink>
</template>
<script setup>
 const props = defineProps({
   to: String,
   class: String,
 });
</script>
