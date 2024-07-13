<script setup lang="ts">

import {onMounted} from "vue";
const redirectCall = () => {
  return window.location.href = `http://localhost:5137/contact`
}

const capItems = [
  {
    id: 1,
    title: 'Core Competencies',
    section: 'competency',
    content: [
        'Caledonia Consulting, LLC. (CC) provides strategic consulting technology services and managed services to commercial, not for profit and government organizations. Our Consulting can mobilize the right people, skills and tech- nologies to help organizations improve their performance.',
        'As a Minority Owned Small Business with HUBZone certification, CC is committed to excellence and creating innovative and flexible solutions for our State and Federal clients.'
    ]
  },
  {
    id: 2,
    title: 'Why Choose Caledonia Consulting?',
    section: 'why',
    content: [
        // 'We speak the language of the technologies of today and tomorrow',
        'A diverse background with over a decade of professional experience',
        'Familiarity with multiple vendor arenas',
        'Strategic partnerships that can be leveraged at a moment’s notice',
        'No outsourcing; our staff is in-house and committed to your success.',
        'You’re working with Certified Project Managers who operate well in and out of structure'
    ]
  },
  {
    id: 3,
    title: 'Past Performance',
    section: 'performance',
    content: [
        'HHS — 5 years as a contractor',
        'DOD — 1 year as a contractor',
        '10 years of consulting on Back End & Front End Application Builds for private'
    ]
  },
  {
    id: 4,
    title: 'Company Data',
    section: 'data',
    content: [
        'Caledonia Consulting (CC) provides consultation ser- vices to the government, small- and medium-sized companies. Our services include technical operations management, technical solution consulting, digital and internet-based consulting to improve the techno- logical footprint of our clients.'
    ]
  },
  {
    id: 5,
    title: 'Codes & Certs',
    section: 'certs',
    content: [
        'DUNS: 118981529',
        'CAGE: 9PHT2',
        'NAICS: 513210, 541511, 541512, 518210, 519290, 561410',
        'Socio-economic certifications: HUBZone, MBE',
        'Accept Credit and Purchase Cards',
        'PMI – CAPM Since ‘18'
    ]
  }
]

onMounted(() => {
  const options = {
    threshold: .50
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        console.log('entry isIntersecting: ', entry)
        entry.target.classList.add('show')
        return
      } else {
        entry.target.classList.remove('show')
        return
      }
    })
  }, options)

  const pageElementArr = Array.from(document.querySelectorAll('.slide'))

  pageElementArr.forEach((el: any) => observer.observe(el))
})

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
          <div v-for="(item, index) in capItems" class="cap-single">
            <div class="cap-title">{{item.title}}</div>
            <div :id="item.section" v-for="content in item.content">
              <div class="cap-content">{{content}}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="slide">
        <div class="container__service"> <!-- Tiles of the tech I know -->
          <button id="contact" @click="console.log('the service section')">Service Offering Section</button>
          <!-- BUILD ROW -->
          <!-- BUILD CELL -->
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

.slide {
  .cap-single {
    opacity: 0;
    transition: all 1s;
  }

  &.show {
    .container__capability {
      .cap-single:nth-child(1) {
        opacity: 1;
        transition: all 1.75s;
      }
      .cap-single:nth-child(2) {
        opacity: 1;
        transition: all 2.5s;
      }
      .cap-single:nth-child(3) {
        opacity: 1;
        transition: all 3.25s;
      }
      .cap-single:nth-child(4) {
        opacity: 1;
        transition: all 4.5s;
      }
      .cap-single:nth-child(5) {
        opacity: 1;
        transition: all 5s;
      }
    }
  }
}

.cap-single {
  height: 20vh;
}

.cap-title {
  font-weight: 700;
}
</style>