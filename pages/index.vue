<template>
  <div>
    <div class="main">
      <!-- Banner -->
      <div class="hero w-full h-[550px]">
        <div class="w-10/12 max-w-screen-xl h-full mx-auto flex items-center justify-between">
          <div class="left text-center sm:text-left">
            <div class="sm:px-6">
              <h2 class="text-5xl sm:text-7xl font-bold">Bienvenue sur <span class="logo">Dev-x</span></h2>
              <p class="text-xl sm:text-2xl text-gray-700 mt-5">Découvre, apprends, progresse !</p>
            </div>
          </div>
          <div class="right hidden md:block">
            <div>
              <img src="@/assets/svg/croods.svg" alt="">
            </div>
          </div>
        </div>
      </div>
      <!-- Last article -->
      <div class="main-content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl px-6 mx-auto">
        <div class="last-article-card mt-16">
          <h4 class="underline decoration-sky-500 decoration-wavy font-extrabold text-2xl">Dernier article publié</h4>
          <div class="last-card flex flex-col-reverse md:flex md:flex-row md:items-center mt-10 w-11/12 mx-auto md:w-full h-auto border-2 shadow-lg rounded-lg">
            <div class="left p-4 w-full md:w-1/2 h-full rounded-lg">
              <h1 class="text-2xl sm:text-3xl md:text-4xl font-medium">Comment réaliser rapidement son portfolio sans code avec Notion</h1>
              <p class="text-md sm:text-lg text-gray-400 font-medium mt-4">Date de publication : 07 Janvier 2022</p>
            </div>
            <div class="right bg-sky-300 p-4 w-full md:w-1/2 h-full rounded-lg">
              
            </div>
          </div>
        </div>
      </div>
      <!-- Articles recents -->
      <div class="recent-main-content w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-24">
        <h4 class="underline decoration-violet-600 pl-6 decoration-wavy font-extrabold text-2xl">Articles récents</h4>
        <div class="recent-articles mt-10 w-10/12 mx-auto md:w-full md:flex md:flex-wrap md:items-center md:justify-between lg:flex lg:items-center lg:justify-around h-auto">
          <div class="recent-article-card mb-10 md:w-[45%] lg:w-[30%] h-full border-2 border-gray-100 rounded-lg shadow-lg">
            <div class="top h-64 bg-red-100"></div>
            <div class="bottom p-3">
              <h1 class="text-2xl font-medium">Comment réaliser rapidement son portfolio sans code avec Notion</h1>
              <p class="text-md text-gray-400 font-medium mt-2">Date de publication : 07 Janvier 2022</p>
            </div>
          </div>
          <div class="recent-article-card mb-10 md:w-[45%] lg:w-[30%] h-full border-2 border-gray-100 rounded-lg shadow-lg">
            <div class="top h-64 bg-red-100"></div>
            <div class="bottom p-3">
              <h1 class="text-2xl font-medium">Comment réaliser rapidement son portfolio sans code avec Notion</h1>
              <p class="text-md text-gray-400 font-medium mt-2">Date de publication : 07 Janvier 2022</p>
            </div>
          </div>
          <div class="recent-article-card mb-10 md:w-[45%] lg:w-[30%] h-full border-2 border-gray-100 rounded-lg shadow-lg">
            <div class="top h-64 bg-red-100"></div>
            <div class="bottom p-3">
              <h1 class="text-2xl font-medium">Comment réaliser rapidement son portfolio sans code avec Notion</h1>
              <p class="text-md text-gray-400 font-medium mt-2">Date de publication : 07 Janvier 2022</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.hero {
  background: url('@/assets/images/hero.jpg');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

@media (max-width: 490px) {
  .main-content, .recent-main-content {
    width: 100%;
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
