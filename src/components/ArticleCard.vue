<script setup lang="ts">
import { useArticleStore } from '../stores/articles';
const store = useArticleStore();
const { setArticle } = store
</script>

<template>
  <div class="p-4">
    <router-link
      :to="`/article/${article.id}`"
      @click="`${setArticle(article.id)}`"
      class="font-bold prose btn-ghost text-xl mb-2"
    >
    {{ article.title }}
    <p class="text-sm">{{ article.content.substring(0, 100) }}...</p>
    <span class="text-xs">{{ article.category }}</span>
    </router-link>
    <span class="divider m-0"></span>
  </div>
</template>

<script lang="ts">
import { useArticleStore } from '../stores/articles';
import { defineComponent } from 'vue';
import { Article } from '../data/articles';

export default defineComponent({
  props: {
    article: {
      type: Object as () => Article,
      required: true,
    },
  },
});
</script>
