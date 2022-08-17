<template>
  <div class="blog-article-preview bg-white shadow sm:rounded-lg p-6">
    <div class="blog-article-preview__title">
      {{ article.title }}
    </div>
    <div class="blog-article-preview__description">
      {{ article.description }}
    </div>
    <div class="blog-article-preview__footer">
      <div>
        <span
          v-for="tag in article.tags"
          :key="tag"
          class="blog-article-preview__tag"
        >
          {{ tag }}
        </span>
      </div>
      <div class="blog-article-preview__created-at">
        Created at {{ createdAt }}
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'BlogArticlePreview',
  props: {
    article: {
      type: Object,
      required: true
    }
  },
  computed: {
    createdAt () {
      const createdAt = new Date(this.article.createdAt)
      return createdAt.toLocaleDateString('en-US')
    }
  }
}

</script>

<style lang="scss">

.blog-article-preview {

  &__title {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  &__description {
    font-size: 0.8rem;
    margin-top: 1rem;
  }

  &__created-at {
    flex: 0 0 50%;
    text-align: right;
  }

  &__footer {
    display: flex;
    justify-content: space-between;
    margin-top: 1rem;
    font-size: 0.8rem;
    color: #999;
  }

  &__tag {
    margin-right: 0.5rem;
  }
}
</style>
