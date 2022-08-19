<template>
  <div class="default-layout">
    <nav>
      <ul class="default-layout__nav">
        <li class="default-layout__nav-items">
          <router-link class="default-layout__nav-item-home" to="/">
            <HomeLogo class="default-layout__logo fill-green-400 hover:fill-green-700" />
          </router-link>
          <router-link class="default-layout__nav-item-blog" to="/blog">
            <BlogLogo class="default-layout__logo fill-green-400 hover:fill-green-700" />
          </router-link>
          <router-link class="default-layout__nav-item-cv" to="/cv">
            <CvLogo class="default-layout__logo fill-green-400 hover:fill-green-700" />
          </router-link>
        </li>
      </ul>
    </nav>
    <main
      class="bg-gray-100 p-6 default-layout__container"
      :class="$route.name"
    >
      <Nuxt />
    </main>
  </div>
</template>

<script>
import HomeLogo from '~/assets/home.svg?inline'
import BlogLogo from '~/assets/blog.svg?inline'
import CvLogo from '~/assets/cv.svg?inline'

export default ({
  name: 'DefaultLayout',
  components: {
    HomeLogo,
    BlogLogo,
    CvLogo
  }
})
</script>

<style lang="scss">
.default-layout {

  &__nav {
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  &__nav-items {
    width: 80%;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  &__logo {
    width: 36px;
    height: 36px;

    .nuxt-link-exact-active &, .default-layout__nav-item-blog.nuxt-link-active & {
      fill: #15803d;
    }
  }

  &__container {
    min-height: calc(100vh - 60px);

    &.index {
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }

}
</style>
