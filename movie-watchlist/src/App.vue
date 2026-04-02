<script setup>
import { ref, computed } from 'vue'

const movies = ref([])
const newMovie = ref('')
const filter = ref('all')

const addMovie = () => {
  if (newMovie.value.trim()) {
    movies.value.push({ title: newMovie.value.trim(), watched: false })
    newMovie.value = ''
  }
}

const toggleWatched = (index) => {
  movies.value[index].watched = !movies.value[index].watched
}

const removeMovie = (index) => {
  movies.value.splice(index, 1)
}

const filteredMovies = computed(() => {
  if (filter.value === 'watched') return movies.value.filter(m => m.watched)
  if (filter.value === 'unwatched') return movies.value.filter(m => !m.watched)
  return movies.value
})

const stats = computed(() => {
  const total = movies.value.length
  const watched = movies.value.filter(m => m.watched).length
  const remaining = total - watched
  return `${total} movies — ${watched} watched — ${remaining} remaining`
})
</script>

<template>
  <div>
    <h1>Movie Watchlist</h1>
    <input v-model="newMovie" @keyup.enter="addMovie" placeholder="Enter movie title">
    <button @click="addMovie">Add</button>

    <div>
      <button @click="filter = 'all'" :class="{ active: filter === 'all' }">All</button>
      <button @click="filter = 'watched'" :class="{ active: filter === 'watched' }">Watched</button>
      <button @click="filter = 'unwatched'" :class="{ active: filter === 'unwatched' }">Unwatched</button>
    </div>

    <ul v-if="filteredMovies.length">
      <li v-for="(movie, index) in filteredMovies" :key="index">
        <span :class="{ watched: movie.watched }">{{ movie.title }}</span>
        <button @click="toggleWatched(movies.indexOf(movie))">
          {{ movie.watched ? 'Unmark' : 'Mark watched' }}
        </button>
        <button @click="removeMovie(movies.indexOf(movie))">Remove</button>
      </li>
    </ul>
    <p v-else>No movies yet. Add one above!</p>

    <p>{{ stats }}</p>
  </div>
</template>

<style scoped>
.watched {
  text-decoration: line-through;
}

.active {
  font-weight: bold;
}
</style>
