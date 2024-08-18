<template>
  <main class="w-full text-center p-6">
    <div class="border-4">
      <h1 class="text-5xl font-bold py-12">My Projects</h1>
    </div>
    <div class="text-left w-full pt-4">
      <template v-for="(project, index) in projects">
      <div v-if="!expanded[index][0]" :id="project.name" class="cursor-pointer mb-4 flex flex-col border-2 items-center sm:flex-row" @click="() => expanded[index] = [true, 0]">
        <div class="p-2 sm:pr-0">
          <span class="font-bold pr-4">{{ project.name }}</span><span class="pr-1">{{ project.start }}</span>-<span class="pl-1">{{ project.end }}</span><br />
          <span>{{ project.goal }}</span><br />
          <p v-html="project.details" class="line-clamp-5"></p>
          <p><span v-for="more_item in project.more"><MoreLink :to="more_item[1]">{{ more_item[0] }}</MoreLink></span></p>
        </div>
        <div class="p-2 h-full">
          <img :src="'/images/' + project.images[0]" :alt="project.name" class="max-h-[12rem] max-w-[12rem] min-w-[6rem] object-cover" />
        </div>
      </div>
      <div v-else class="cursor-pointer mb-4 border-2 p-2" @click="() => expanded[index] = [false, 0]">
        <span class="font-bold pr-4">{{ project.name }}</span><span class="pr-1">{{ project.start }}</span>-<span class="pl-1">{{ project.end }}</span><br>
        <span>{{ project.goal }}</span><br />
        <p v-html="project.details"></p>
        <br>
        <div class="flex flex-row sm:gap-5 items-stretch w-100 items-center justify-center">
          <div v-if="expanded[index][1] > 0" class="flex w-10 text-center items-center justify-items-center bg-slate-200 animate-pulse cursor-pointer" @click="(event) => {event.stopPropagation(); expanded[index][1]--; }">
            <p class="w-full rotate-180">&#10140</p>
          </div>
          <div v-else class="flex w-10"></div>
          <img :src="'/images/' + project.images[expanded[index][1]]" class="flex max-h-[16rem] max-w-[32rem] min-w-[10rem]"/>
          <div v-if="expanded[index][1] < project.images.length - 1" class="flex w-10 text-center items-center justify-items-center bg-slate-200 animate-pulse cursor-pointer" @click="(event) => {event.stopPropagation(); expanded[index][1]++; }">
            <p class="w-full">&#10140</p>
          </div>
          <div v-else class="flex w-10">
          </div>
        </div>
        <br>
        <p><span v-for="more_item in project.more"><MoreLink :to="more_item[1]">{{ more_item[0] }}</MoreLink></span></p>
      </div>
      </template>
    </div>
  </main>
</template>

<script setup>
 import projects from "@/assets/data/projects.json"
 
 var expanded = ref(projects.map(() => [false, 0]));
 
</script>
