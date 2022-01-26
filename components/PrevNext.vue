<template>
  <div>
    <div class="prev-next w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-16">
      <hr>
      <div class="contain w-96 mx-auto mt-4 flex items-center justify-around bg-green-400">
        <NuxtLink
          v-if="prev"
          :to="`${prev.slug}`"
          class="font-bold text-primary hover:underline"
        >
          <button class="w-44 h-9 font-medium text-md outline-none text-white font-medium bg-black shadow-md shadow-black/50 rounded-lg">
            Arrticle precédent
          </button>
        </NuxtLink>
        <span v-else>&nbsp;</span>
        <NuxtLink
          v-if="next"
          :to="`${next.slug}`"
          class="font-bold hover:underline"
        >
          <button class="w-44 h-9 font-medium text-md outline-none text-white bg-black shadow-md shadow-black/50 rounded-lg">
            Article suivant
          </button>
        </NuxtLink>
        <span v-else></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null
    },
    next: {
      type: Object,
      default: () => null
    }
  }
}
</script>

<style scoped>
@media (max-width: 410px) {
  .
}
</style>