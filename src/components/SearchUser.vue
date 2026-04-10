<template>
  <div class="search-container">
    <input
      type="text"
      placeholder="Search industry leaders..."
      @input="$emit('search', $event.target.value)"
      class="search-input"
    />
  </div>
</template>

<style scoped>
.search-container {
  margin-bottom: 30px;
  display: flex;
  justify-content: center;
}

.search-input {
  background: #2d521c;
  border: 2px solid #3b7428;
  padding: 12px 20px;
  border-radius: 25px;
  color: white;
  width: 300px;
  outline: none;
  transition: border-color 0.3s;
}

.search-input:focus { 
  border-color: #8c1c00;
}

::placeholder {
  color: #3b7428;
}

</style>