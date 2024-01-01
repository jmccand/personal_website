<template>
  <main class="w-full text-center p-6">
    <div class="border-4">
      <h1 class="text-5xl font-bold py-12">My Projects</h1>
    </div>
    <table class="text-left border-separate border-spacing-y-4">
      <tbody>
	<tr v-for="project in projects">
	  <td class="border-2 border-r-0 p-2">
	    <span class="font-bold pr-4">{{ project.name }}</span><span class="pr-1">{{ project.start }}</span>-<span class="pl-1">{{ project.end }}</span><br />
	    <span>{{ project.goal }}</span><br />
	    <p v-html="project.details"></p>
	    <p><span class="font-bold">More:</span><span v-for="more_item in project.more" v-html="' ' + more_item"></span></p>
	  </td>
	  <td class="border-2 border-l-0 p-2">
	    <img :src="'/_nuxt/assets/images/' + project.thumbnail" :alt="project.name">
	  </td>
	</tr>
      </tbody>
    </table>
  </main>
</template>

<script setup>
 import projects from "@/assets/data/projects.json"
</script>
