<template>
  <v-app-bar
    v-scroll="onScroll"
    :color="!isScrolling ? 'transparent' : 'white'"
    fixed
    flat
  >
    <v-slide-x-transition>
      <!-- <v-img
        v-if="showLogo"
        :src="require('@/assets/logo.png')"
        class="shrink"
        contain
        height="50"
      /> -->
      <div v-if="showLogo">
        <span class="shrink headline red--text text--darken-4">
          Parroquia San Sebastián de Ocú
        </span>
      </div>
    </v-slide-x-transition>

    <v-spacer />

    <social-media />
  </v-app-bar>
</template>

<script>
  export default {
    name: 'CoreAppBar',

    components: {
      SocialMedia: () => import('@/components/SocialMedia'),
    },

    data: () => ({
      showLogo: false,
      isScrolling: false,
    }),

    methods: {
      onScroll () {
        const offset = window.pageYOffset
        this.isScrolling = offset > 50
        this.showLogo = offset > 200
      },
    },
  }
</script>
