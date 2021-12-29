<template>
  <div>
    <div class="navbar fixed top-0 w-full h-16 bg-black shadow-lg">
      <div class="main w-11/12 h-full mx-auto flex items-center justify-between">
      <!-- Left -->
        <div class="logo pl-4 sm:w-auto h-full flex items-center justify-between">
          <h1 class="text-white font-medium text-4xl px-3 py-5 flex items-center justify-center">
            <nuxt-link to="/" class="mt-1">Dev-x</nuxt-link>
          </h1>
          <div class="burger-btn">
            <svg class="ham hamRotate ham1" viewBox="0 0 100 100" width="70" onclick="this.classList.toggle('active')" @click="() => slideMenu = !slideMenu">
              <path
                class="line top"
                d="m 30,33 h 40 c 0,0 9.044436,-0.654587 9.044436,-8.508902 0,-7.854315 -8.024349,-11.958003 -14.89975,-10.85914 -6.875401,1.098863 -13.637059,4.171617 -13.637059,16.368042 v 40" />
              <path
                class="line middle"
                d="m 30,50 h 40" />
              <path
                class="line bottom"
                d="m 30,67 h 40 c 12.796276,0 15.357889,-11.717785 15.357889,-26.851538 0,-15.133752 -4.786586,-27.274118 -16.667516,-27.274118 -11.88093,0 -18.499247,6.994427 -18.435284,17.125656 l 0.252538,40" />
            </svg>
          </div>
        </div>
        <!-- Right -->
        <div class="main-content h-full text-white flex items-center">
          <div class="menu-items z-20">
            <ul class="inline">
              <li class="inline mx-2">
                <nuxt-link to="/" class="px-2 py-px text-lg">Accueil</nuxt-link>
              </li>
              <li class="inline mx-2">
                <nuxt-link to="/articles" class="px-2 py-px text-lg">Articles</nuxt-link>
              </li>
            </ul>
          </div>
          <div class="search-bar ml-4 md:ml-8 flex items-center relative">
            <input type="text" name="search" id="search" placeholder="Rechercher..." class="bg-gray-200 hidden md:h-8 md:pl-4 text-black text-md md:outline-none md:rounded-lg md:block">
            <button class="bg-gray-200 w-8 p-2 rounded-lg outline-none border-none block md:hidden cursor-pointer z-30" @click="() => visibleSearchBar = !visibleSearchBar">
              <img src="@/assets/svg/search.svg" alt="search icon">
            </button>
            <input :class="visibleSearchBar ? 'show-search-bar' : 'hide-search-bar'" type="text" name="search" id="search" placeholder="Rechercher..." class="absolute top-0 right-0 bg-gray-200 h-10 pl-4 text-black text-md outline-none shadow-xl rounded-lg">
          </div>
          <div class="social-items hidden lg:flex lg:items-center lg:ml-8">
            <div class="icon mx-2">
              <a href="https://www.linkedin.com/in/adamsaimedesireofficial/"><img src="@/assets/svg/linkedin-alt.svg" alt="linkedin icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://github.com/DevDams"><img src="@/assets/svg/github-alt.svg" alt="github icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://twitter.com/dams9ix"><img src="@/assets/svg/twitter-alt.svg" alt="twitter icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://www.instagram.com/dams9ix/"><img src="@/assets/svg/instagram-alt.svg" alt="instagram icon"></a>
            </div>
          </div>
        </div>
        <!-- Mobile menu -->
        <div :class="slideMenu ? 'show-menu' : 'hide-menu'" class="mobile-main-content bg-black flex flex-col items-center justify-center shadow-lg">
          <div class="menu-items z-20">
            <ul class="inline text-white">
              <li class="block my-2">
                <nuxt-link to="/" class="px-2 py-px text-xl">Accueil</nuxt-link>
              </li>
              <li class="block my-2">
                <nuxt-link to="/articles" class="px-2 py-px text-xl">Articles</nuxt-link>
              </li>
            </ul>
          </div>
          <div class="search-bar mt-4 mb-2 flex items-center relative w-full">
            <input type="text" name="search" id="search" placeholder="Rechercher..." class="bg-gray-200 w-[80%] h-10 mx-auto pl-4 text-black text-md outline-none border border-gray-100 shadow-sm rounded-lg block">
          </div>
          <div class="social-items flex items-center mt-4">
            <div class="icon mx-2">
              <a href="https://www.linkedin.com/in/adamsaimedesireofficial/"><img src="@/assets/svg/linkedin-alt.svg" alt="linkedin icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://github.com/DevDams"><img src="@/assets/svg/github-alt.svg" alt="github icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://twitter.com/dams9ix"><img src="@/assets/svg/twitter-alt.svg" alt="twitter icon"></a>
            </div>
            <div class="icon mx-2">
              <a href="https://www.instagram.com/dams9ix/"><img src="@/assets/svg/instagram-alt.svg" alt="instagram icon"></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      visibleSearchBar: false,
      slideMenu: false,
    }
  },
}
</script>

<style scoped>
.logo h1 {
  font-family: 'Horta';
  line-height: 0;
}

.show-search-bar {
  top: 60px;
  right: 0;
  opacity: 1;
  border: 2px solid rgba(0, 0, 0, 0.788);
  transition: .3s all ease;
}

.hide-search-bar {
  top: 0;
  opacity: 0;
  transition: .3s all ease;
  z-index: 0;
}

.burger-btn {
  display: none;
}

.mobile-main-content {
  display: none;
}

@media (max-width: 490px) {
  .logo {
    width: 100%;
  }

  .logo h1 {
    font-size: 30px;
  }

  .burger-btn {
    display: block;
  }

  /* css for burger button */
  .ham {
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
    transition: transform 400ms;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }
  .hamRotate.active {
    transform: rotate(45deg);
  }
  .hamRotate180.active {
    transform: rotate(180deg);
  }
  .line {
    fill:none;
    transition: stroke-dasharray 400ms, stroke-dashoffset 400ms;
    stroke:#fff;
    stroke-width:5.5;
    stroke-linecap:round;
  }
  .ham1 .top {
    stroke-dasharray: 40 139;
  }
  .ham1 .bottom {
    stroke-dasharray: 40 180;
  }
  .ham1.active .top {
    stroke-dashoffset: -98px;
  }
  .ham1.active .bottom {
    stroke-dashoffset: -138px;
  }

  .main-content {
    display: none;
  }

  .hide-menu.mobile-main-content {
    display: none;
    position: absolute;
    top: 0rem;
    left: 0;
    width: 100%;
    height: 250px;
    transition: .3s top ease;
  }

  .show-menu.mobile-main-content {
    display: flex;
    position: absolute;
    top: 3.9rem;
    left: 0;
    width: 100%;
    height: 250px;
    transition: .3s top ease;
  }
}
</style>
