<template>
  <div>
    List of entries
    <li v-for="article in articles" :key="article.slug">
      <router-link :to="`/blog/${article.slug}`">
        {{ article.title }}
      </router-link>
    </li>
  </div>
</template>

<script lang="ts">
import { Context } from '@nuxt/types'

export default {
  name: 'BlogIndex',
  async asyncData ({ $content }: Context) {
    const articles = await $content('articles')
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles
    }
  }
}
</script>
