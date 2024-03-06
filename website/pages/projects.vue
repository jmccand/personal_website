<template>
  <main class="w-full text-center p-6">
    <div class="border-4">
      <h1 class="text-5xl font-bold py-12">My Projects</h1>
    </div>
    <div class="text-left w-full pt-4">
      <template v-for="project in projects">
	<div :id="project.name" class="cursor-pointer mb-4 flex flex-col sm:flex-row border-2 items-center" @click="update_displayed_project(project.name)">
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
    <div v-if="displayed_project != null" id="popup" class="text-left rounded-md border-4 fixed bg-white right-4 left-4 height-0 top-0 p-4 overflow-y-scroll transition-all duration-1000" :style="{ top: targetTop+'px', height: targetHeight+'px' }">
      <span class="font-bold pr-4">{{ displayed_project.name }}</span><span class="pr-1">{{ displayed_project.start }}</span>-<span class="pl-1">{{ displayed_project.end }}</span><span class="absolute right-4 top-4 font-sans cursor-pointer p-2" @click="close_popup()">&#9587</span> <br />
      <span>{{ displayed_project.goal }}</span><br />
      <p v-html="displayed_project.details"></p>
      <br />
      <div class="flex flex-row gap-5 items-stretch w-100 items-center justify-center">
	<div v-if="displayed_image_index > 0" class="flex w-10 text-center items-center justify-items-center bg-slate-200 animate-pulse cursor-pointer" @click="displayed_image_index--">
	  <p class="w-full rotate-180">&#10140</p>
	</div>
	<div v-else class="w-10">
	</div>
	<img :src="'/images/' + displayed_project.images[displayed_image_index]" class="max-h-[16rem] max-w-[30rem] min-h-[10rem] object-cover">
	<div v-if="displayed_image_index < displayed_project.images.length - 1" class="flex w-10 text-center items-center justify-items-center bg-slate-200 animate-pulse cursor-pointer" @click="displayed_image_index++">
	  <p class="w-full">&#10140</p>
	</div>
	<div v-else class="w-10">
	</div>
      </div>
      <br />
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
 var displayed_image_index = ref(null);

 async function update_displayed_project(elem_id) {
   var displayed_elem = document.getElementById(elem_id);
   displayed_project.value = findProjectByName(elem_id);
   displayed_image_index.value = 0;
   var rect = displayed_elem.getBoundingClientRect();
   // show initial box
   targetTop.value = rect.top - 10;
   targetHeight.value = displayed_elem.offsetHeight;
   
   // prevent scrolling
   document.body.style.overflow = "hidden";

   // wait for box to be displayed on DOM
   await nextTick();
   setTimeout(() => {
     // expand popup
     targetTop.value = 80;
     targetHeight.value = innerHeight - targetTop.value - 40;
   }, 5);
 }

 async function close_popup() {
   displayed_project.value = null;
   displayed_image_index.value = 0;
   document.body.style.overflow = "auto";
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
