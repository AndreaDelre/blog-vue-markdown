<template>
  <div class="home">
    <h1>Posts du blog</h1>
    <div class="blog__legend blog__section">📝 article - 📺 conférence - 🤝 organisateur</div>
    <div class="blog__period blog__section" v-for="(period, index) in POSTS" :key="index">
      <h2>{{period.name}}</h2>

      <div class="blog__period__article" v-for="(post, index_bis) in period.posts" :key="index_bis">
        <span class="post-type">{{post.type}} - </span>
        <span class="title" v-if="post.type !== 'article'">
          <a :href="post.url" target="_blank">{{post.title}}</a>
        </span>
        <span class="title" v-else>
          <router-link
            :to="'/' + post.folder + '/' + post.url">
            {{post.title}}
          </router-link>
        </span>
        <span class="date"> - {{post.created_date}}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import POSTS from '@/posts/posts.json';
</script>
