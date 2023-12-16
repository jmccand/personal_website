<template>
  <!-- common layout for each page -->
  <div>
    
    <!-- define header -->
    <header>
      <!-- navigation links -->
      <nav>
	<ul>
	  <li><NuxtLink to="/about">About Me</NuxtLink></li>
	  <li><NuxtLink to="/mission">Mission</NuxtLink></li>
	  <li><NuxtLink to="/projects">Projects</NuxtLink></li>
	  <li><NuxtLink to="/collaboration">Social</NuxtLink></li>
	  <li><NuxtLink to="/timeline">Timeline</NuxtLink></li>
	</ul>
      </nav>
    </header>

    <body style="min-height: 85vh">
      <!-- page content -->
      <NuxtPage />
    </body>

    <!-- define footer -->
    <footer>
      <p>Contact Me!</p>
    </footer>
    
  </div>
</template>
