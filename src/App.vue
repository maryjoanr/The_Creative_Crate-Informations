<template>
  <main class="app-container">
    <header>
      <h1>The Creative Crate</h1>
    </header>

    <SearchUser @search="handleSearch" />
    
    <p v-if="loading">Fetching industry leaders...</p>
    <UserList v-else :users="filteredUsers" />
  </main>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import SearchUser from './components/SearchUser.vue'
import UserList from './components/UserList.vue'

const searchQuery = ref('')
const users = ref([])  
const loading = ref(true) 


const getApiData = async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    const data = await response.json()

    users.value = data.map(item => ({
      id: item.id,
      name: item.name,
      industry: item.company.bs, 
      email: item.email,
      phone: item.phone,
      image: `https://i.pravatar.cc/150?u=${item.id}` 
    }))
  } catch (error) {
    console.error("Error loading API:", error)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  getApiData()
})

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

body {
  margin: 0;
  font-family: 'Inter', sans-serif;
  background-color: #531301;
}

.app-container {
  padding: 50px 20px;
  text-align: center;
  color: white;
}

.accent {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  color: #8c1c00;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 40px;
}

</style>