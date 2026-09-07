<script setup>
import LayoutCard from '@/components/LayoutCard.vue'
import portfolioData from '@/data/portfolio.json'

const images = import.meta.glob('@/assets/*.{jpg,jpeg,png,webp,svg}', {
  eager: true,
  import: 'default',
})

const getImage = (filename) => {
  const path = Object.keys(images).find((path) => path.endsWith(`/${filename}`))
  return path ? images[path] : ''
}
</script>

<template>
  <div>
    <LayoutCard
      v-for="item in portfolioData"
      :key="item.id"
      :image="getImage(item.thumbnail)"
      :title="item.title"
      :description="item.description"
      :medium="item.medium"
      :created="item.created"
      :course="item.course"
      :showNav="true"
    />
  </div>
</template>
