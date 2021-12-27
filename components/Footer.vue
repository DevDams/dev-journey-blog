<template>
  <div>
    <div class="footer w-full h-12 border-t border-t-gray-200 mt-32 bg-gray-50">
      <div class="container w-11/12 h-full mx-auto flex items-center justify-between">
        <div class="copyright">
          <p class="font-medium">&copy; 2022 Tous droits réservés</p>
        </div>
        <div class="custom-text">
          <p class="font-medium">Contruit avec ♥ par <span class="underline decoration-rose-500 decoration-wavy"><a href="http://damsx.netlify.app" target="_blank">Aimé</a></span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
@media (max-width: 475px) {
  .footer {
    height: 4.1rem;
  }

  .container {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
}
</style>
