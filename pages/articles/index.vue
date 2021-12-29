<template>
  <div>
    <div class="main">
      <div class="header pt-32 w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl px-6 mx-auto">
        <h1 class="text-3xl sm:text-5xl font-bold text-center">Tout les articles</h1>
        <div class="categories mt-10 text-center flex flex-col items-center justify-center">
          <h4 class="text-lg font-semibold underline decoration-wavy">Catégories:</h4>
          <ul class="inline flex flex-wrap items-center justify-around mt-2">
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-gray-500 shadow-md shadow-gray-500/50">Code Snipped</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-orange-500 shadow-md shadow-orange-500/50 bg-white">Javascript</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-indigo-500 shadow-md shadow-indigo-500/50">CSS/TailwindCss</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-green-500 shadow-md shadow-green-500/50">Vue.js/Nuxtjs</li>
            <li class="cursor-pointer inline-block px-2 py-1 text-sm text-white mx-1 mt-3 rounded-full bg-white bg-rose-500 shadow-md shadow-rose-500/50">Packages/Plugins</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>