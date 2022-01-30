<template>
  <div>
    <div class="prev-next w-11/12 md:w-10/12 lg:w-9/12 max-w-screen-xl mx-auto mt-16">
      <hr>
      <div class="contain mx-auto mt-4 flex justify-between">
        <div class="w-1/2 text-left">
          <NuxtLink
            v-if="prev"
            :to="`${prev.slug}`"
            class="font-bold"
          >
            <p>Article précédent:</p>
            <button class="font-medium text-left text-md outline-none text-rose-400 font-medium hover:underline">
              {{ prev.title }}
            </button>
          </NuxtLink>
          <p v-else>Pas d'article précédent</p>
        </div>
        <div class="w-1/2 text-right">
          <NuxtLink
            v-if="next"
            :to="`${next.slug}`"
            class="font-bold"
          >
            <p>Article suivant:</p>
            <button class="font-medium text-right text-md outline-none text-rose-400 hover:underline">
              {{ next.title }}
            </button>
          </NuxtLink>
          <p v-else>Pas d'article suivant</p>
        </div>
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
}
</style>