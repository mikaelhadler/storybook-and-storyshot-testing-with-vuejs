<script>
export default {
  props: {
    article: { type: Object, required: true },
    showAuthor: { type: Boolean, required: false, default: true }
  }
}
</script>

<template>
  <article class="article-card">
    <h2
      v-if="!!article.title"
      class="headline">
      <router-link :to="{ name: 'article', params: { articleId: article.id } }">
        {{ article.title }}
      </router-link>
    </h2>
    <img
      v-if="!!article.imageUrl"
      :src="article.imageUrl"
      class="image-lead">
    <p v-if="showAuthor && !!article.author.name">
      By <router-link :to="{ name: 'author', params: { authorId: article.author.id } }">
        {{ article.author.name }}
      </router-link>
    </p>
    <p
      v-if="!!article.summary"
      class="article.summary">
      {{ article.summary }}
    </p>
  </article>
</template>

<style lang="postcss">
@import url(../assets/vars-include.css);

.article-card {
  margin: 48px 0;

  & p {
    margin-bottom: 16px;
  }

  & .headline {
    margin-bottom: 20px;
    @apply --font-twenty;
    font-weight: bold;
  }

  & .image-lead {
    object-fit: cover;
    object-position: right top;
    max-width: 600px;
    width: 100%;
    max-height: 360px;
    height: 100%;
    margin-bottom: 24px;
    border-radius: 25px;
  }

  & .summary {
    @apply --font-sixteen;
  }
}
</style>
