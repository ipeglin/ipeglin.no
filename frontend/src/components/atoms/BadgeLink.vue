<script setup lang="ts">
interface Props {
  image: string,
  link: string,
}

const props = defineProps<Props>();
</script>

<template>
  <a class="badge-link" target="_blank" :href="link">
    <img class="badge-image accent" :src="image" loading='lazy' />
  </a>
</template>

<style scoped lang="scss">
.badge-image {
    width: 25px;
    height: 25px;
  }
</style>