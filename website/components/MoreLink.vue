<template>
  <NuxtLink :to="props.to" target="_blank" class="border-l-2 px-2 items-center min-w-fit">
    <slot>
    </slot>
  </NuxtLink>
</template>
<script setup>
 const props = defineProps({
   to: String
 });
</script>
