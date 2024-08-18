<script setup lang="ts">
import { useWindowSize } from '@vueuse/core'


import {onMounted} from "vue";

const { height, width } = useWindowSize()

const capItems = [
  {
    id: 0,
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
    id: 1,
    title: 'Past Performance',
    section: 'performance',
    content: [
        'HHS — 5 years as a contractor',
        'DOD — 1 year as a contractor',
        '10 years of consulting on Back End & Front End Application Builds for private'
    ]
  }
]

const codesAndCerts = [
  {
    id: 0,
    title: 'Codes & Certs',
    section: 'certs',
    content: [
      'DUNS: 118981529',
      'CAGE: 9PHT2',
      'NAICS: 513210, 541511, 541512, 518210, 519290, 561410','541430',
      'SBA certifications: HUBZone, MBE',
      'PMI: CAPM (2018-present)'
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
  <div v-if="width > 900" class="container__landing--desktop">
    <div class="container__content--container">
      <div class="slide one">
        <div class="top">
          <div class="left">
            <img src="https://cdn-s3.touchofmodern.com/products/000/515/683/595ab994e1d64a66c15662041fcf685e_large.jpg" class="landing-image"/>
          </div>
          <div class="right">
            <div class="container__content--text">
              <div class="company-title">
                <span class="primary">CALEDONIA</span>
                <span class="underline"></span>
                <span class="secondary">CONSULTING LLC</span>
              </div>
              <div class="container__cta--desktop">
                <span>Contact Us Icon</span>
              </div>
            </div>
          </div>
        </div>
        <div  class="bottom">
          <div class="cap-title">Company Data</div>
          <div class="cap-content">As a Minority-Owned Small Business with HUBZone certification, Caledonia Consulting is committed to excellence when creating innovative and flexible solutions for our state, federal, and commercial clients.</div>
          <div class="cap-content">Our services include technical operations management, technical solutions consulting, and digital and internet-based consulting to improve the technological footprint of our clients.</div>
          <img class="arrowdown" src="/arrowdown.svg">
        </div>
      </div>
      <div class="slide two">
        <div class="container__capability">
          <div v-for="(item) in capItems" class="cap-single">
            <div class="cap-title">{{item.title}}</div>
            <div :id="item.section" :class="item.section" v-for="content in item.content">
              <div class="cap-content"><span class="bullet" v-if="item.section === 'why' || item.section === 'certs' || item.section === 'performance' ">&#x2022</span>{{content}}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="slide three">
        <div class="container__testimonials">
          <div class="cap-title">Testimonials</div>
          <p class="testimonial">"Caledonia Consulting did an outstanding job for me on website design and development. Everything was customized to my requirements, and the resulting site is appealing, highly intuitive, and user-friendly. I would recommend Caledonia to anyone seeking expert guidance in setting up their business website."</p>
          <p class="testimonial"> - Pinkert Trade & Human Rights Consulting</p>
        </div>
      </div>
      <div class="slide four">
        <div class="container__codes">
          <div class="cap-single">
            <div class="cap-title">{{codesAndCerts[0].title}}</div>
            <div :id="codesAndCerts[0].section" :class="codesAndCerts[0].section" v-for="content in codesAndCerts[0].content">
              <div class="cap-content"><span class="bullet">&#x2022</span>{{content}}</div>
            </div>
          </div>
          <div class="cap-single">
            <div class="container__contact">
              <div class="cap-title">Contact</div>
              Email: <a href="mailto:hello@caledoniallc.io" rel="noopener noreferrer">hello@caledoniallc.io</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-else class="container__landing--mobile">
    <div class="container__content--container">
      <div class="slide one">
        <div class="container__content--text">
          <div class="company-title">
            <span class="primary">CALEDONIA</span>
            <span class="underline"></span>
            <span class="secondary">CONSULTING LLC</span>
          </div>
          <div class="container__cta--desktop">
            <span>Contact Us Icon</span>
          </div>
        </div>
      </div>
      <div class="slide two">
        <div v-for="(item) in capItems" class="cap-single">
          <div class="cap-title">{{item.title}}</div>
          <div :id="item.section" :class="item.section" v-for="content in item.content">
            <div class="cap-content"><span class="bullet" v-if="item.section === 'why' || item.section === 'certs' || item.section === 'performance' ">&#x2022</span>{{content}}</div>
          </div>
        </div>
      </div>
      <div class="slide four">
        <div class="container__codes">
          <div class="cap-single">
            <div class="cap-title">{{codesAndCerts[0].title}}</div>
            <div :id="codesAndCerts[0].section" :class="codesAndCerts[0].section" v-for="content in codesAndCerts[0].content">
              <div class="cap-content"><span class="bullet">&#x2022</span>{{content}}</div>
            </div>
          </div>
          <div class="cap-single">
            <div class="container__contact">
              <div class="cap-title">Contact</div>
              Email: <a href="mailto:hello@caledoniallc.io" rel="noopener noreferrer">hello@caledoniallc.io</a>
            </div>
          </div>
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

.container__contact {
  text-align: center;

  a {
    color: white;
  }
}

.landing-image {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.bullet {
  margin-right: 5px;
  font-weight: 900;
}

.slide {
 height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;

  .cap-title {
    margin-top: 20px;
  }

  &.two {
    height: 100%;
  }

  &.three {
    height: 100%;
    min-height: 250px;
  }

  &.four {
    height: 100%;
    min-height: 250px;
  }

  .top {
    display: flex;
    flex-direction: row;
  }

  .left {
    width: 50vw;
    position: relative;
    height: 60vh;
  }

  .right {
    width: 50vw;
    justify-content: center;
    align-items: center;
    display: flex;
    height: 60vh;
    background: #0065bd;

    .container__cta--desktop {
      display: none;
    }

    .company-title {
      font-family: "Nunito Sans", sans-serif;
      font-weight: 700;
      font-size: 40px;
      color: #FFF;
      display: flex;
      flex-direction: column;
      text-align: center;

      .primary {
        font-size: 55px;
      }

      .underline {
        height: 7px;
        width: 100%;
        background-color: white;
        margin-bottom: 7px;
      }

      .secondary {
        font-size: 30px;
      }
    }
  }

  .bottom {
    display: flex;
    flex-direction: column;
    width: 65%;
    margin: 0px auto 0;
    text-align: center;

    .arrowdown {
      margin: 25px 0 0 0;
      height: 60px;
      opacity: .6;
    }
  }
}

.slide {
  .cap-single {
    opacity: 0;
    transition: all 1s;

    .competency {
      padding-left: 5px;
    }
  }

  .container__capability {
    color: #121212;
    display: flex;

    .slide {
      flex-direction: column;
    }
  }

  &.show {
    .container__capability {

      min-height: 350px;

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

  .container__codes {
    display: flex;
    .cap-single {
      opacity: 1;
      transition: all 1.75s;
    }
  }
}

.slide:nth-child(1) {
  display: flex;

  .cap-content {
    font-size: 20px;
    line-height: 1.95rem;
  }
}

.slide:nth-child(2) {
  .cap-title {
    padding-bottom: 10px;
  }
  .cap-single {
    margin-left: 6%;
  }
}

.slide:nth-child(3) {
  background-color: #333e4880;
  color: white;
  font-size: 22px;

  .container__testimonials {
    .testimonial {
      width: 80%;
      margin: 0 auto;
    }

    .cap-title {
      color: white;
    }
  }
}

.slide:nth-child(4) {
  background-color: #0065bd;
  color: white;

  .cap-single {
    margin-left: 6%;
  }

  .cap-title {
    color: white;
  }
}

.cap-single {
  height: 20vh;
  font-size: 18px;
  display: flex;
  flex-direction: column;
  width: 50vw;
}

.cap-title {
  font-weight: 700;
  font-size: 25px;
  color: #0065bd;
  text-align: center;
}

.container__landing--mobile {
  .slide {
    min-height: 100vh;

    &.one {
      width: 100vw;
      justify-content: center;
      align-items: center;
      display: flex;
      background: #0065bd;

      .container__cta--desktop {
        display: none;
      }

      .company-title {
        font-family: "Nunito Sans", sans-serif;
        font-weight: 700;
        font-size: 40px;
        color: #FFF;
        display: flex;
        flex-direction: column;
        text-align: center;

        .primary {
          font-size: 55px;
        }

        .underline {
          height: 7px;
          width: 100%;
          background-color: white;
          margin-bottom: 7px;
        }

        .secondary {
          font-size: 30px;
        }
      }
    }

    &.two {
      background-color: white;
      color: blue;
      min-height: 100vh;

      .cap-single {
        height: 100%;
        font-size: 18px;
        display: flex;
        flex-direction: column;
        width: 98vw;
        color: black !important;
        opacity: 1;
        margin: 0;
        padding-left: 7px;
      }
      justify-content: space-evenly;

      .cap-title {
        font-weight: 700;
        font-size: 25px;
        color: #0065bd;
        text-align: center;
      }
    }

    &.four {

      .container__codes {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        height: 100vh;
        text-align: center;
        * > {
        }
      }

      .cap-single {
        height: 100%;
        width: 100%;
        padding-left: 7px;
      }
    }
  }
}
</style>