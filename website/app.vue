<template>
  <!-- common layout for each page -->
  <div>
    <!-- define header -->
    <header class="flex flex-row p-4 md:text-lg sm:text-base text-sm shadow-lg justify-start items-center">
      <div class="flex flex-col justify-center sm:hidden h-0 cursor-pointer" @click="navbarOpen=!navbarOpen">
        <p class="flex text-xl">&#8801;</p>
      </div>
      <div class="flex flex-row justify-center w-full sm:w-fit">
        <span class="w-auto min-w-fit font-bold sm:pr-10">Joel McCandless</span>
      </div>
      <!-- navigation links -->
      <div class="hidden sm:flex">
        <nav class="container flex">
          <ul class="flex flex-row space-x-8">
            <li><NuxtLink to="/about">About Me</NuxtLink></li>
            <li><NuxtLink to="/mission">Mission</NuxtLink></li>
            <li><NuxtLink to="/projects">Projects</NuxtLink></li>
            <li><NuxtLink to="/social">Social</NuxtLink></li>
          </ul>
        </nav>
      </div>
    </header>
    <div v-if="navbarOpen">
      <nav class="container flex border-b-2 pt-3">
        <ul class="flex flex-col w-full items-center">
          <li class="p-2 pl-4"><NuxtLink to="/about" @click="navbarOpen=false">About Me</NuxtLink></li>
          <li class="p-2 pl-4"><NuxtLink to="/mission" @click="navbarOpen=false">Mission</NuxtLink></li>
          <li class="p-2 pl-4"><NuxtLink to="/projects" @click="navbarOpen=false">Projects</NuxtLink></li>
          <li class="p-2 pl-4"><NuxtLink to="/social" @click="navbarOpen=false">Social</NuxtLink></li>
        </ul>
      </nav>
    </div>

    <body style="min-height: 80vh">
      <!-- page content -->
      <NuxtPage />
    </body>

    <!-- define footer -->
    <footer class="w-full flex flex-col md:flex-row items-center border-t-4 p-4 sm:space-x-4 space-y-2 sm:space-y-0 text-xs lg:text-base">
      <TagLink :to="'https://www.linkedin.com/in/joel-mccandless-a09275273/'">
        <img src="/images/linkedin-icon.png" style="max-height: 3vh" class="sm:pr-2" />
        LinkedIn
      </TagLink>
      <TagLink :to="'https://github.com/jmccand'">
        <img src="/images/github-icon.png" style="max-height: 3vh" class="sm:pr-2" />
        GitHub/Jmccand
      </TagLink>
      <TagLink :to="'mailto:mail@joelmccandless.com'">
        <img src="/images/mail-icon.png" style="max-height: 4vh" class="sm:pr-2" />
        mail@joelmccandless.com
      </TagLink>
      <TagLink :to="'tel:+7812672701'">
        <img src="/images/phone-icon.png" style="max-height: 3vh" class="sm:pr-2" />
        (781) 267-2701
      </TagLink>
      <TagLink :to="'https://goo.gl/maps/QgktqPpbrLqry4Mz9'">
        <img src="/images/location-icon.png" style="max-height: 3vh" class="sm:pr-2" />
        Lexington, MA
      </TagLink>
    </footer>
  </div>
</template>
<script setup>
  var navbarOpen = ref(false);
</script>