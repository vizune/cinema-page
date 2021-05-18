<template>
  <dialog class="Modal" v-bind:open="modalShow">
    <header class="Modal-header">
        <h3 class="Modal-title u-mt-0" v-html="heading" />
        <button class="Modal-close" 
        v-on:click="modalClose"
        title="Close dialog">
            <span class="sr-only">Close</span>
        </button>
    </header>
    <div class="Modal-content">
        <slot />
    </div>
    <footer class="Modal-footer">
        <button class="Button Button--blue" 
        v-on:click="modalClose">
            Close
        </button>
    </footer>
  </dialog>
</template>

<script>
export default {
  data() {
    return {
      modalShow: false
    };
  },
  props: {
    heading: {
      type: String,
      required: true
    }
  },
  methods: {
    modalClose: function() {
      this.modalShow = false;
      this.$emit('modalClosed', true)
    }
  }
};
</script>

<style lang="scss" scoped>
.Modal {
    background-color: #fff;

    @keyframes fadein {
        0% {
            opacity: 0; 
            transform: translate(-50%, .75rem) scale(.95);
        }
        100%  {
            opacity: 1; 
            transform: translateX(-50%);
        }
    }

    @keyframes fadeout {
        0%  {
            opacity: 1; 
            transform: translateX(-50%);
        }
        100% {
            opacity: 0; 
            transform: translate(-50%, .75rem) scale(.95);
        }
    }

    position: fixed;
    top: 20vh;
    left: 50%;
    transform: translateX(-50%);
    border: none;
    box-shadow: 0 16px 48px 16px rgba(0,0,0,0.17);
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    min-width: 320px;
    max-width: 60vh;
    min-height: 235px;
    max-height: 60vh;
    margin: 0;
    padding: 1.5rem;
    visibility: hidden;
    animation: fadeout .3s ease-in-out;
    z-index: 100;
    overflow: hidden;
    
    &[open] {
        visibility: visible;
        animation: fadein .3s ease-in-out;
    }

    &-header {
        display: flex;
        justify-content: space-between;
        width: 100%;
    }

    &-title {
        font-size: 1.25rem;
        padding-right: 1rem;
    }

    &-close {
        display: block;
        position: relative;
        width: 12px;
        height: 12px;
        padding: .75rem;
        margin-right: -.25rem;
        background-color: transparent;
        border: none;
        border-radius: 0;

        &:before, &:after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 12px;
            height: 2px;

            border-radius: 2px;
            background-color: #000;
            display: block;
        }

        &:before {
            transform: translate(-50%, -50%) rotate(45deg);
        }

        &:after {
            transform: translate(-50%, -50%) rotate(-45deg);
        }
    }

     &-content {
         font-size: .75rem;
         margin-bottom: 1.5rem;
         overflow-y: auto;
         overflow-x: hidden;
         max-height: 30vh;
     }

     &-footer {
         align-self: flex-end;
     }
}
</style>