<script setup lang="ts">

const redirectCall = () => {
  return window.location.href = `http://localhost:5137/contact`
}

</script>

<template>
  <div class="container__landing--desktop">
    <div class="container__content--container">
      <span>Landing</span>

      <div class="slide">
        <div class="left">
          <img src="/nasa-Q1p7bh3SHj8-unsplash.jpg" class="landing-image"/>
        </div>
        <div class="right">
          <div class="container__content--text">
            <div class="company-title">CALEDONIA CONSULTING LLC</div>
            <div class="container__cta--desktop">
              <a href="#contact">Contact Us</a>
            </div>
          </div>
        </div>

      </div>
      <div class="slide">
        <div class="container__capability">
          <button @click="console.log('the capability section')">Capability Section</button>
        </div>
      </div>
      <div class="slide">
        <div class="container__service">
          <button id="contact" @click="console.log('the service section')">Service Offering Section</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.container__landing--desktop {
  background-color: #008E97;
}

.container__content--container {
  align-items: center;
}

.landing-image {
  height: 100%;
  width: 100%;
  object-fit: cover;

}

.slide {
 height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: row;

  .left {
    width: 50vw;
  }

  .right {
    width: 50vw;
    justify-content: center;
    align-items: center;
    display: flex;


    .company-title {
      font-family: "Nunito Sans", sans-serif;
      font-weight: 700;
      font-size: 40px;
      color: white;
    }
  }
}
</style>