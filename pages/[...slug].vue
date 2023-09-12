<script setup lang="ts">
const route = useRoute()

const [prev, next] = await queryContent('/')
  .sort({ _file: 1 })
  .where({ show: true })
  .findSurround(route.path)
</script>

<template>
  <main>
    <ContentDoc />
    <hr>
    <div>
      <br>
      <span v-if="prev">
        prev: <NuxtLink  :to="prev._path">{{ prev.title }}</NuxtLink>
      </span>
      <span v-if="prev && next"> | </span>
      <span v-if="next">
        next: <NuxtLink v-if="next" :to="next._path">{{ next.title }}</NuxtLink>
      </span>
      <br>
      <br>
    </div>
  </main>
</template>
