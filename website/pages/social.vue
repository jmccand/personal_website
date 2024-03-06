<template>
  <main class="w-full text-center p-6">
    <div class="text-left w-full pt-4">
      <template v-for="org in organizations">
	<div :id="org.name" class="mb-10 pb-4 flex flex-col items-center text-center border-b-4">
	  <span class="font-bold pr-4">{{ org.name }}</span>
	  <span class="pr-1">{{ org.start + " - " + org.end }}</span>
	  <br />
	  <p v-html="org.details" class="line-clamp-5"></p>
	  <img :src="'/images/' + org.images[0][0]" :alt="org.name" class="max-h-[80vh] max-w-[90vw] object-cover">
	  <br />
	  <p v-html="org.images[0][1]"></p>
	  <br />
	</div>
      </template>
    </div>
  </main>
</template>

<script setup>
 import organizations from "@/assets/data/organizations.json"
 import { ref } from 'vue' 
</script>
