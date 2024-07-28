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
        <div id="landing" class="img__logo" @click="setPage"><img src="/logocc.png" height="50" width="50"></div>
        <div :class="`${width > 600 ? 'container__nav-items--desktop' : 'container__nav-items--mobile'}`">
          <div id="capability" class="nav-item"><a class="nav-item" href="https://drive.google.com/file/d/1kpeoBmJembZu2g6p0op4UOXPCTWvuRGn/view?usp=sharing" target="_blank">CAP STATEMENT</a></div>
          <div id="contact" class="nav-item"><a class="nav-item" href="mailto:caledoniaconsult@gmail.com" rel="noopener noreferrer">CONTACT</a></div>
        </div>
      </div>
    </div>
    <div class="container__content--app">
      <Transition>
        <Landing v-if="activePage === 'landing'" />
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
  background: white;
  color: black;

  > * {
    height: 50px;
    align-items: center;

  }

  a {
    color: black;
  }
}

.container__navbar--desktop {
  position: sticky;


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

    a {
      color: unset;
      font-size: inherit;
      font-family: inherit;
    }
  }

  .container__nav-items--mobile {
    display: flex;
    flex-direction: row;
    width: 100vw;
    justify-content: space-evenly;
  }

}

.container__content--app {
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
