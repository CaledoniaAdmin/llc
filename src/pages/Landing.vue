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
          <div class="container__testimonials">
            <p class="testimonial">"Caledonia Consulting did an outstanding job for me on website design and development. Everything was customized to my requirements, and the resulting site is appealing, highly intuitive, and user-friendly. I would recommend Caledonia to anyone seeking expert guidance in setting up their business website."  07/06/2024
            </p>
          </div>
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
  background-color: #FFF;
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
    position: relative;

    .container__testimonials {
      position: absolute;
      bottom: 40%;
      padding:  15px;
      background-color: black;

      .testimonial {
        color: white;
      }
    }
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
      color: #008E97;
    }
  }
}
</style>