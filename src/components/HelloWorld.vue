<template>
  <div class="container mt-5">
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Phone</th>
          <th>Address</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="artist in artists" :key="artist.name">
          <td>{{ artist.name }}</td>
          <td>{{ artist.phone }}</td>
          <td>{{ artist.address }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      artists: [],
    }
  },
  mounted() {
    axios
      .get('./data.json')
      .then((response) => {
        this.artists = response.data
      })
      .catch((error) => {
        console.error('Error:', error)
      })
  },
}
</script>
