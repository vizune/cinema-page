<template>
    <a href="#" class="HeroBanner-link"
    v-on:click.prevent="changeName(name)"
    v-bind:class="{'is-selected' : selected}">
        <span 
        class="HeroBanner-bullet"
        v-bind:style="{
            animationDelay: animationDelay,
            animationDuration: animationDuration
        }">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" xml:space="preserve">
            <path fill="none" stroke="#FFBA21" stroke-width="2" stroke-linejoin="round" stroke-miterlimit="10" d="M16 5.1l2.9 8.9h9.4l-7.6 5.5 2.9 9-7.6-5.6-7.6 5.6 2.9-9L3.7 14h9.4z"/></svg>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" xml:space="preserve">
            <path fill="none" stroke="#FFBA21" stroke-width="2" stroke-linejoin="round" stroke-miterlimit="10" d="M16 5.1l2.9 8.9h9.4l-7.6 5.5 2.9 9-7.6-5.6-7.6 5.6 2.9-9L3.7 14h9.4z"/></svg>
        </span>
    </a>
</template>

<script>
export default {
  props: {
    url: String,
    delay: String,
    duration: String,
    name: String,
    selected: {
        type: Boolean,
        default: false
    }
  },
  computed: {
      animationDelay: function() {
          return Math.floor(Math.random() * (-.85 - .2 + 1) + .2) + "s";
      },
      animationDuration: function() {
          return Math.floor(Math.random() * (.6 - .2 + 1) + .2) + "s";
      }
  },
  methods: {
        changeName (value) {
            this.$emit('clicked', value)
        }
  }
}
</script>

<style lang="scss" scoped>
$color: #FFBA21;

.HeroBanner {
    &-link {
        display: block;
        width: 100px;
        height: 100px;

        &:before {
			content: "";
			text-align: center;
			height: 100%;
			width: 3px;
			display: inline-block;
			background: #555;
			position: relative;
			left: 50%;
            transform: translateX(-50%);
            transition: background-color .2s ease-in-out, box-shadow .2s ease-in-out;
            z-index: 0;
		}

        &:first-child,
        &:last-child {
            height: 50vh;
        }

        &:nth-child(2),
        &:nth-child(8) {
            height: 40vh;
        }

        &:nth-child(3),
        &:nth-child(7) {
            height: 30vh;
        }

        &:nth-child(4),
        &:nth-child(6) {
            height: 20vh;
        }

        &:nth-child(5) {
            height: 10vh;
        }

        &:hover {

            &:before {
                background: $color;
                box-shadow: -1px 0 6px 1px #FFBA21;
            }
        }
    }
         
    @keyframes keyframes1 {
        0% {
            transform: rotate(-1deg);
            animation-timing-function: ease-in;
        }
        50% {
            transform: rotate(1.5deg);
            animation-timing-function: ease-out;
        }
    }
        
    @keyframes keyframes2 {
        0% {
            transform: rotate(1deg);
            animation-timing-function: ease-in;
        }
        50% {
            transform: rotate(-1.5deg);
            animation-timing-function: ease-out;
        }
    }

    &-bullet {
        position: relative;
        display: block;
        width: 4rem;
        height: 4rem;
        margin: -1.25rem auto 0;
        transform-origin: center center;
        transition: transform .5s ease-in-out;

        .HeroBanner-link:nth-child(2n) & {
            animation-name: keyframes1;
            animation-iteration-count: infinite;
            transform-origin: 50% 10%;
        }

        .HeroBanner-link:nth-child(2n-1) & {
            animation-name: keyframes2;
            animation-iteration-count: infinite;
            animation-direction: alternate;
            transform-origin: 30% 5%;
        }

        svg:last-child {
            position: absolute;
            opacity: .5;
            transition: transform .3s ease-in-out .1s;
            top: 0;
            transform-origin: center;
        }

        .HeroBanner-link:hover & {
            animation: none;

            svg:last-child {
                opacity: 0.5;
                transform: scale(1.25);
            }
        }

        .HeroBanner-link.is-selected & {
            svg:last-child {
                opacity: 0.5;
                transform: scale(1.25);
            }
        }
    }
}
</style>
