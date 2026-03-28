<template>
  <main class="app-container">
    <header>
      <h1>Partnered with <span class="accent">Twelve Midnight</span></h1>
    </header>

    <SearchUser @search="handleSearch" />
    
    <UserList :users="filteredUsers" />
  </main>
</template>

<script setup>
import { ref, computed } from 'vue'
import SearchUser from './components/SearchUser.vue'
import UserList from './components/UserList.vue'

const searchQuery = ref('')

const users = ref([
  { 
    id: 1, 
    name: 'Bae Nara', 
    industry: 'Music & Performance', 
    bio: 'Renowned artist specializing in stage presence and vocal mastery.', 
    image: new URL('./assets/BaeNara.jpg', import.meta.url).href 
  },
  { 
    id: 2, 
    name: 'Choi Hyun Wook', 
    industry: 'Acting', 
    bio: 'Award-winning actor known for versatile roles in modern drama.', 
    image: new URL('./assets/ChoiHyunWook.jpg', import.meta.url).href 
  },
  { 
    id: 3, 
    name: 'Daniella', 
    industry: 'Fashion', 
    bio: 'Leading the new wave of global fashion and branding.', 
    image: new URL('./assets/Daniella.jpg', import.meta.url).href 
  },
  { 
    id: 4, 
    name: 'Park Ji Hoon', 
    industry: 'Entertainment', 
    bio: 'A powerhouse in the global entertainment and idol industry.', 
    image: new URL('./assets/ParkJiHoon.jpg', import.meta.url).href 
  }
])

const handleSearch = (query) => {
  searchQuery.value = query
}

const filteredUsers = computed(() => {
  return users.value.filter(user => 
    user.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
    user.industry.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;600&family=Playfair+Display:ital@1&display=swap');

body { margin: 0; font-family: 'Inter', sans-serif; background-color: #531301; }
.app-container { padding: 50px 20px; text-align: center; color: white; }
.accent { font-family: 'Playfair Display', serif; font-style: italic; color: #8c1c00; }
h1 { font-size: 2.5rem; margin-bottom: 40px; }
</style>