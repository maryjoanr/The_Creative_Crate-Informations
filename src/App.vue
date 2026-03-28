<template>
  <main class="app-container">
    <header>
      <h1>The Creative Crate</h1>
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
    industry: 'Human Resources', 
    email: 'baenara098@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/BaeNara.jpg', import.meta.url).href 
  },
  { 
    id: 2, 
    name: 'Choi Hyun Wook', 
    industry: 'Information Technology', 
    email: 'choihyunwookashayichan@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/ChoiHyunWook.jpg', import.meta.url).href 
  },
  { 
    id: 3, 
    name: 'Daniela Avanzini', 
    industry: 'Marketing', 
    email: 'katseyedaniela@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Daniella.jpg', import.meta.url).href 
  },
  { 
    id: 4, 
    name: 'Lara Raj', 
    industry: 'Marketing', 
    email: 'katseyelararaj@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Lara.jpg', import.meta.url).href 
  },
  { 
    id: 5, 
    name: 'Manon Bannerman', 
    industry: 'Finances & Accounting', 
    email: 'katseyemanon@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Manon.jpg', import.meta.url).href 
  },
  { 
    id: 6, 
    name: 'Megan Skiendiel', 
    industry: 'Finances & Accounting', 
    email: 'katseyemegan8@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Megan.jpg', import.meta.url).href 
  },
  { 
    id: 7, 
    name: 'Park Ji Hoon', 
    industry: 'Information Technology', 
    email: 'parkjihon099@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/ParkJiHoon.jpg', import.meta.url).href 
  },
  { 
    id: 8, 
    name: 'Ryeoun', 
    industry: 'Operations', 
    email: 'ryeoun94@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Ryeoun.jpg', import.meta.url).href 
  },
  { 
    id: 9, 
    name: 'Seol In Ah', 
    industry: 'Operations', 
    email: 'seolinah@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/SeolInAh.jpg', import.meta.url).href 
  },
  { 
    id: 10, 
    name: 'Shin Eun Soo', 
    industry: 'Human Resources', 
    email: 'eunsoo@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/ShinEunSoo.jpg', import.meta.url).href 
  },
  { 
    id: 11, 
    name: 'Sophia Laforteza', 
    industry: 'Sales', 
    email: 'katseyesofia@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Sophia.jpg', import.meta.url).href 
  },
  { 
    id: 12, 
    name: 'Jeung Yoonchae', 
    industry: 'Sales', 
    email: 'katseyeyoonchae@yahoo.com',
    phone: '+63 765 945 3556' ,
    image: new URL('./assets/Yoonchae.jpg', import.meta.url).href 
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