<template>
  <div>
    <div class="main">
      <!-- Banner -->
      <div class="hero w-full h-[550px]">
        <div class="w-10/12 max-w-screen-xl h-full mx-auto flex items-center justify-between">
          <div class="left text-center sm:text-left">
            <div class="sm:px-6">
              <h2 class="text-5xl sm:text-7xl font-bold">Bienvenue sur dev-x</h2>
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
      <!-- <div class="main-content w-9/12 max-w-screen-xl px-6 mx-auto">
        <div class="last-article-card mt-16">
          <h4 class="font-medium text-2xl text-rose-500">Dernier article publié</h4>
          <div class="last-card mt-8 w-full h-[300px] border shadow-lg rounded-lg"></div>
        </div>
      </div> -->
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
</style>
