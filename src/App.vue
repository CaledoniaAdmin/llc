<script setup lang="ts">
import {ref} from "vue";
import { useWindowSize } from '@vueuse/core'


// NAV
import Landing from "./pages/Landing.vue";
import Capability from "./pages/Capability.vue";
import Contact from "./pages/Contact.vue";
import Ticker from "./pages/Ticker.vue";

const activePage = ref('landing')
const { width } = useWindowSize();

const setPage = (e: Event) => {
  console.log('e: ', (e.target as HTMLElement).id)
  activePage.value = (e.target as HTMLElement).id
}

</script>

<template>
  <div class="container__overlay--desktop">
    <div class="container__navbar--desktop">
      <div class="container__navbar--container">
        <div id="landing" class="img__logo" @click="setPage">LOGO</div>
        <div :class="`${width > 600 ? 'container__nav-items--desktop' : 'container__nav-items--mobile'}`">
          <div id="capability" class="nav-item" @click="setPage">CAPABILITIES</div>
          <div id="contact" class="nav-item" @click="setPage">CONTACT</div>
          <div id="ticker" class="nav-item" @click="setPage">TICKER</div>
        </div>
      </div>
    </div>
    <div class="container__content--main">
      <Transition>
        <Landing v-if="activePage === 'landing'" />
      </Transition>
      <Transition>
        <Capability v-if="activePage === 'capability'" />
      </Transition>
      <Transition>
        <Contact v-if="activePage === 'contact'" />
      </Transition>
      <Transition>
        <Ticker v-if="activePage === 'ticker'" />
      </Transition>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fira+Sans:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,opsz,wght@0,6..12,200..1000;1,6..12,200..1000&display=swap');
.container__overlay--desktop {
  height: 100vh;
  width: 100vw;
}

.container__navbar--container {
  display: flex;
  flex-direction: row;
  width: 100vw;
  font-family: "Fira Sans", sans-serif;
  font-weight: 500;
  font-style: normal;
  background: black;


  > * {
    height: 50px;
    align-items: center;

  }
}

.container__navbar--desktop {
  position: absolute;


  .container__nav-items {
    display: flex;
    flex-direction: row;
    margin-left: 50%;
    width: 100vw;
    justify-content: space-evenly;
  }

  .container__nav-items--desktop {
    display: flex;
    flex-direction: row;
    margin-left: 50%;
    width: 100vw;
    justify-content: space-evenly;
  }

  .container__nav-items--mobile {
    display: flex;
    flex-direction: row;
    width: 100vw;
    justify-content: space-evenly;
  }

}

.container__content--main {
  color: black;

  /* All incoming content */
  > * {
    display: flex;
    justify-content: center;
    width: 100vw;
    align-items: center;
  }
}
</style>
