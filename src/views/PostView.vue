<template>
  <div class="post">
    <Markdown class="post__content" :source="postMakdown" />
  </div>
</template>
<script setup>
import { useRoute } from 'vue-router';
import Markdown from 'vue3-markdown-it';

const route = useRoute();

const { year, url } = route.params;

// eslint-disable-next-line
const postMakdown = require(`../posts/${year}/${url}.md`).default;
</script>
