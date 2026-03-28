<template>
  <div class="card">
    <img :src="image" alt="profile" class="pic" />
    <div class="label">
      <h4>{{ name }}</h4>
      <p>{{ industry }}</p>
    </div>
    <div class="hover-overlay">
      <h4>{{ name }}</h4>
      <div class="line"></div>
      <p class="bio-text">{{ bio }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps(['name', 'industry', 'image', 'bio'])
</script>

<style scoped>
.card {
  width: 220px; height: 300px; border-radius: 12px;
  position: relative; overflow: hidden; background: #2d521c;
}
.pic { width: 100%; height: 100%; object-fit: cover; }
.label {
  position: absolute; bottom: 0; width: 100%; padding: 15px;
  background: linear-gradient(transparent, #2d521c); color: white;
}
.hover-overlay {
  position: absolute; top: 0; left: 0; width: 100%; height: 100%;
  background: #531301; padding: 20px; opacity: 0; transition: 0.4s; color: white;
}
.card:hover .hover-overlay { opacity: 1; }
.line { width: 30px; height: 2px; background: #8c1c00; margin: 10px 0; }
.bio-text { font-size: 0.8rem; line-height: 1.4; }
</style>