<template>
  <main class="w-full text-center p-6">
    <div class="border-4">
      <h1 class="text-5xl font-bold py-12">My Projects</h1>
    </div>
    <div class="text-left w-full pt-4">
      <div v-for="project in projects" class="mb-4 flex flex-col sm:flex-row border-2 items-center">
	<div class="p-2 pr-0">
	  <span class="font-bold pr-4">{{ project.name }}</span><span class="pr-1">{{ project.start }}</span>-<span class="pl-1">{{ project.end }}</span><br />
	  <span>{{ project.goal }}</span><br />
	  <p v-html="project.details" class="line-clamp-5"></p>
	  <p><span class="font-bold pr-2">More</span><span v-for="more_item in project.more"><MoreLink :to="more_item[1]">{{ more_item[0] }}</MoreLink></span></p>
	</div>
	<div class="p-2 h-full">
	  <img :src="'/_nuxt/assets/images/' + project.thumbnail" :alt="project.name" class="max-h-[12rem] max-w-[12rem] min-w-[6rem] object-cover">
	</div>
      </div>
    </div>
  </main>
</template>

<script setup>
 import projects from "@/assets/data/projects.json"
</script>
