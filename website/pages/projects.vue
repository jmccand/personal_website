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
    <div v-if="displayed_project != null" id="popup" class="text-left rounded-md border-4 fixed bg-white right-4 left-4 height-0 top-0 p-4 overflow-hidden transition-all duration-1000" :style="{ top: targetTop+'px', height: targetHeight+'px' }">
      <span class="font-bold pr-4">{{ displayed_project.name }}</span><span class="pr-1">{{ displayed_project.start }}</span>-<span class="pl-1">{{ displayed_project.end }}</span><br />
      <span>{{ displayed_project.goal }}</span><br />
      <p v-html="displayed_project.details"></p>
      <p><span class="font-bold pr-2">More</span><span v-for="more_item in displayed_project.more"><MoreLink :to="more_item[1]">{{ more_item[0] }}</MoreLink></span></p>
    </div>
  </main>
</template>

<script setup>
 import projects from "@/assets/data/projects.json"
 import { ref, onUpdated, nextTick } from 'vue'

 var targetTop = ref(80);
 var targetHeight = ref(60);
 var displayed_project = ref(null);

 async function update_displayed_project(elem_id) {
   var displayed_elem = document.getElementById(elem_id);
   displayed_project.value = findProjectByName(elem_id);
   var rect = displayed_elem.getBoundingClientRect();
   // show initial box
   targetTop.value = rect.top - 10;
   targetHeight.value = displayed_elem.offsetHeight;

   // wait for box to be displayed on DOM
   await nextTick();
   setTimeout(() => {
     // expand popup
     targetTop.value = 80;
     targetHeight.value = innerHeight - targetTop.value - 80;
   }, 5);
 }

 function findProjectByName(elem_id) {
   for (const [index, element] of projects.entries()) {
     if (element.name == elem_id) {
       return element;
     }
   }
   return null;
 }
 
</script>
