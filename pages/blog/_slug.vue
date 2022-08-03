<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>

    <img :src="article.img" :alt="article.alt" />

    <p>Article last updated: {{ article.updatedAt }}</p>

    <nuxt-content :document="article" />
  </article>
</template>

<script lang='ts'>
import { Context } from '@nuxt/types'

export default {
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
