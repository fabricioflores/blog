<template>
  <div class="blog-index">
    <div v-for="article in articles" :key="article.slug">
      <router-link :to="`/blog/${article.slug}`">
        <BlogArticlePreview :article="article" />
      </router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { Context } from '@nuxt/types'

export default {
  name: 'BlogIndex',
  async asyncData ({ $content }: Context) {
    const articles = await $content('articles')
      .only(['title', 'description', 'slug', 'createdAt', 'tags'])
      .sortBy('createdAt', 'desc')
      .fetch()

    return {
      articles
    }
  }
}
</script>

<style lang="scss">
.blog-index {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);

  @include for-tablet-landscape-up {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
