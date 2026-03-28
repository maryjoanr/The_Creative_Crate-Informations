<template>
  <div class="list-wrapper">
    <div v-if="users.length > 0" class="grid">
      <UserCard 
        v-for="user in users" 
        :key="user.id" 
        v-bind="user" 
      />
    </div>
    <p v-else class="no-results">No partners found...</p>
  </div>
</template>

<script setup>
import UserCard from './UserCard.vue'
defineProps(['users'])
</script>

<style scoped>
.grid { display: flex; flex-wrap: wrap; gap: 20px; justify-content: center; }
.no-results { color: #3b7428; margin-top: 20px; }
</style>