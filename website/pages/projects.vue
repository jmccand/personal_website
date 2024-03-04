<template>
  <main class="w-full text-center p-6">
    <div class="border-4">
      <h1 class="text-5xl font-bold py-12">My Projects</h1>
    </div>
    <div class="text-left w-full pt-4">
      <template v-for="project in projects">
	<div :id="project.name" class="mb-4 flex flex-col sm:flex-row border-2 items-center" @click="update_displayed_project(project.name)">
	  <div class="p-2 pr-0">
	    <span class="font-bold pr-4">{{ project.name }}</span><span class="pr-1">{{ project.start }}</span>-<span class="pl-1">{{ project.end }}</span><br />
	    <span>{{ project.goal }}</span><br />
	    <p v-html="project.details" class="line-clamp-5"></p>
	    <p><span class="font-bold pr-2">More</span><span v-for="more_item in project.more"><MoreLink :to="more_item[1]">{{ more_item[0] }}</MoreLink></span></p>
	  </div>
	  <div class="p-2 h-full">
	    <img :src="'/images/' + project.images[0]" :alt="project.name" class="max-h-[12rem] max-w-[12rem] min-w-[6rem] object-cover">
	  </div>
	</div>
      </template>
    </div>
    <div v-if="displayed_project != null" id="popup" class="rounded-md border-4 fixed bg-white right-6 left-6" :style="{ top: targetTop+'px', height: targetHeight+'px' }">
      <div class="absolute top-0 left-0 right-0 text-center" :html="displayed_project.name">
      </div>
    </div>
  </main>
</template>

<script setup>
 import projects from "@/assets/data/projects.json"
 import { ref } from 'vue'

 var displayed_project = ref(null);
 var targetTop = ref(80);
 var targetHeight = ref(60);

 function update_displayed_project(elem_id) {
   console.log("update called!");
   displayed_project.value = document.getElementById(elem_id);
   var rect = displayed_project.value.getBoundingClientRect();
   targetTop.value = rect.top;
   targetHeight.value = displayed_project.value.offsetHeight;
   console.log("update done! ");
   console.log(displayed_project.value);
   console.log(targetTop.value);
   console.log(targetBottom.value);
 }
 
</script>
