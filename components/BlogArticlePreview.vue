<template>
  <div class="blog-article-preview bg-white shadow sm:rounded-lg p-6">
    {{ article.title }}
  </div>
</template>

<script lang="ts">

export default {
  name: 'BlogArticlePreview',
  props: {
    article: {
      type: Object,
      required: true
    }
  }
}

</script>
