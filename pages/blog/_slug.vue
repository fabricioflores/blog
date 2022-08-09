<template>
  <article class="blog-article">
    <h2 class="blog-article__title">
      {{ article.title }}
    </h2>

    <p class="blog-article__description">
      {{ article.description }}
    </p>

    <img class="blog-article__image" :src="article.img" :alt="article.alt">

    <nuxt-content class="blog-article__content" :document="article" />
  </article>
</template>

<script lang='ts'>
import { Context } from '@nuxt/types'

export default {
  name: 'BlogArticle',
  async asyncData ({ $content, params, error }: Context) {
    try {
      const article = await $content('articles', params.slug).fetch()
      return { article }
    } catch (e) {
      error({ statusCode: 404, message: 'Not found' })
    }
  }
}
</script>

<style lang="scss">

.blog-article {

  &__title {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 1rem;
  }

  &__description {
    margin-bottom: 1rem;
    font-style: italic;
  }

  &__image {
    max-width: 25%;
    margin: 1rem auto;
  }

  &__content {
    font-size: 1rem;
    margin: 1rem 0;

    h3 {
      font-size: 1.2rem;
      font-weight: bold;
      margin: 1rem 0 0.5rem;
    }

    img {
      max-width: 50%;
      margin: 1rem auto;
    }

    ul, ol {
      margin: 1rem 2rem;
    }

    ul {
      @apply list-disc;
    }

    ol {
      @apply list-decimal;
    }

    a {
      @apply text-green-400;

      &:hover {
        @apply text-green-700;
      }
    }
  }
}

</style>
