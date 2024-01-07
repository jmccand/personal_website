<template>
  <!-- common layout for each page -->
  <div>
    
    <!-- define header -->
    <header class="flex flex-row p-4 space-x-10 md:text-lg sm:text-base text-sm shadow-lg">
      <span class="w-auto min-w-fit font-bold">Joel McCandless</span>
      <!-- navigation links -->
      <nav class="container flex">
	<ul class="flex flex-row space-x-8">
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
    <footer class="w-full flex flex-col md:flex-row items-center border-t-4 p-4 space-x-4 space-y-2 text-xs lg:text-base">
      <div class="pr-4">Contact Me!</div>
      <TagLink :to="'mailto:mail@joelmccandless.com'">
	<img src="/images/mail-icon.png" style="max-height: 4vh" class="pr-2">
	mail@joelmccandless.com
      </TagLink>
      <TagLink :to="'https://github.com/jmccand'">
	<img src="/images/github-icon.png" style="max-height: 3vh" class="pr-2">
	GitHub/Jmccand
      </TagLink>
      <TagLink :to="'tel:+7812672701'">
	<img src="/images/phone-icon.png" style="max-height: 3vh" class="pr-2">
	(781) 267-2701
      </TagLink>
      <TagLink :to="'https://www.linkedin.com/in/joel-mccandless-a09275273/'">
	<img src="/images/linkedin-icon.png" style="max-height: 3vh" class="pr-2">
	LinkedIn
      </TagLink>
      <TagLink :to="'https://goo.gl/maps/QgktqPpbrLqry4Mz9'">
	<img src="/images/location-icon.png" style="max-height: 3vh" class="pr-2">
	Lexington, MA
      </TagLink>
    </footer>
    
  </div>
</template>
