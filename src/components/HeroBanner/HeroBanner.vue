<template>
    <div class="HeroBanner">
        <div class="HeroBanner-decoration">
            <hero-banner-item 
            v-for="item in data" 
            :key="item.name"
            :name="item.name"
            @clicked="onClickChangeName"
            :selected="item.name === heading" />
        </div>
        <div class="HeroBanner-content">
            <h1 class="HeroBanner-title">
                <span>{{heading}}</span>
                <span>with</span>
                <img src="/assets/images/logo.png" width="250px">
            </h1>
        </div>
        <div class="HeroBanner-image">
        </div>
    </div>
</template>

<script>
import HeroBannerItem from './HeroBanner-item.vue'

export default {
  components: { HeroBannerItem },
  name: 'HeroBanner',
  data() {
      return {
          heading: null,
      }
  },
  props: {
    title: String,
    imgSrc: String,
    imgDescription: String,
    data: Array
  },
  mounted() {
      this.heading = this.title;
  },
  methods: {
      onClickChangeName (value) {
        this.heading = value;
    },
  }
}
</script>

<style lang="scss" scoped>
$color: #FFBA21;

.HeroBanner {
    background: #334982;
    position: relative;
    z-index: 5;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 100%;
    overflow: hidden;

    &:before {
        content: '';
        position: absolute;
        top: 0;
        bottom: 0;
        right: 0;
        left: 0;
        background: linear-gradient(to right, rgb(245, 100, 0) 0%, rgb(255, 0, 0) 25%, rgb(181, 0, 125) 50%, rgb(33, 66, 156) 75%, rgb(0, 113, 255) 100%);
        opacity: .25;
    }


    &-content {
        position: absolute;
        bottom: 0;
        z-index: 3;

        @media (min-width: 1024px) {
            bottom: 0;
            top: 35vh;
        }
    }

    &-title {
        color: #fff;
        font-weight: bold;
        font-size: 2.5rem;
        font-family: 'Ubuntu','Montserrat', sans-serif;
        text-align: center;
        text-transform: uppercase;
        letter-spacing: 5px;
        text-shadow: 0 1px 0 #ccc, 0 2px 0 #c9c9c9, 0 3px 0 #bbb, 0 4px 0 #b9b9b9, 0 5px 0 #aaa, 0 6px 1px rgba(0,0,0,.1), 0 0 5px rgba(0,0,0,.1), 0 1px 3px rgba(0,0,0,.3), 0 3px 5px rgba(0,0,0,.2), 0 5px 10px rgba(0,0,0,.25), 0 20px 20px rgba(0,0,0,.15);
        z-index: 1;

        @media (min-width: 1024px) {
            font-size: 4rem;
        }

        img {
            margin: -2rem auto 0;
        }

        span:first-child {
            display: block;
        }

        span:last-child {
            font-size: 2rem;

            @media (min-width: 1024px) {
                font-size: 3rem;
            }
        }
    }

    &-decoration {
        width: 100%;
        display: flex;
        justify-content: space-between;
        position: absolute;
        top: 0;
        padding: 0;
        z-index: 2;

        @media (min-width: 1024px) {
            padding: 0 3rem;
        }
    }

    &-image {
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        opacity: .3;
        z-index: 1;
        background-image: url("/assets/images/sky2.jpg");
        background-attachment: fixed;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
    }

    &-divider {
        width: 100%;
        position: absolute;
        bottom: 0;
    }
}
</style>