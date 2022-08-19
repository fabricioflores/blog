<!-- Please remove this file from your project -->
<template>
  <div class="home flex justify-center items-center">
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <div class="bg-white shadow sm:rounded-lg p-6">
        <h2 class="text-2xl leading-7 font-semibold">
          Fabricio Flores
        </h2>
        <h3 class="mt-4">
          Software Developer at <a target="_blank" href="https://www.bairesdev.com/">BairesDev</a>
        </h3>
        <div class="mt-4">
          <p class="text-gray-500">
            I'm a software developer based in Loja, Ecuador.
          </p>
          <p class="text-gray-500">
            I like code, video games and soccer.
          </p>
          <div class="home__links">
            <a class="home__link hover:fill-green-700" target="_blank" href="https://www.linkedin.com/in/fabricio-flores/">
              <LinkedInLogo />
            </a>
            <a class="home__link hover:fill-green-700" target="_blank" href="https://www.github.com/fabricioflores/">
              <GithubLogo />
            </a>
            <a class="home__link hover:fill-green-700" target="_blank" href="https://www.twitter.com/fabricioflores/">
              <TwitterLogo />
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GithubLogo from '~/assets/github.svg?inline'
import LinkedInLogo from '~/assets/linkedin.svg?inline'
import TwitterLogo from '~/assets/twitter.svg?inline'

export default {
  name: 'BlogHome',
  components: {
    GithubLogo,
    LinkedInLogo,
    TwitterLogo
  }
}
</script>

<style lang="scss">

.home {

  &__links {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 2rem;
  }

  &__link {
    width: 36px;
    height: 36px;
    margin-right: 8px;
  }
}
</style>
