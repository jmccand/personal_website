<template>
  <!-- common layout for each page -->
  <div>
    
    <!-- define header -->
    <header class="p-4 shadow-lg">
      <!-- navigation links -->
      <nav class="container flex">
	<ul class="flex space-x-8">
	  <li><NuxtLink to="/about">About Me</NuxtLink></li>
	  <li><NuxtLink to="/mission">Mission</NuxtLink></li>
	  <li><NuxtLink to="/projects">Projects</NuxtLink></li>
	  <li><NuxtLink to="/social">Social</NuxtLink></li>
	  <li><NuxtLink to="/timeline">Timeline</NuxtLink></li>
	</ul>
      </nav>
    </header>

    <body style="min-height: 80vh">
      <!-- page content -->
      <NuxtPage />
    </body>

    <!-- define footer -->
    <footer class="w-full flex flex-row items-center border-t-4 p-4">
      <div class="pr-4">Contact Me!</div>
      <ul class="flex space-x-8">
	<li>
	  <NuxtLink to="https://github.com/jmccand" target="_blank" class="border-2 rounded-md p-2 flex flex-row items-center">
	    <img src="@/assets/images/github-icon.png" style="max-height: 4vh" class="pr-2">
	    Jmccand
	  </NuxtLink>
	</li>
      </ul>
    </footer>
    
  </div>
</template>
