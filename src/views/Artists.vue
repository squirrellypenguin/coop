

<template>
  <div class="container-fluid">
   <div class="gallery"> 
    <div v-for="(artist, index) in artists" :key=index>
    <p>{{ artist.gsx$profilepicture.$t }}</p>
    <p>{{ artist.gsx$name.$t }}</p>
    <p>{{ artist.gsx$about.$t }}</p>
    <p>{{ artist.gsx$description.$t }}</p>
    <p>{{ artist.gsx$email.$t }}</p>
    <p>{{ artist.gsx$website.$t }}</p>
    <p>{{ artist.gsx$images.$t }}</p>
   </div>
   </div>

 </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
export default {
  name: 'Artists',
  components: {
    
  },

 data() {
    return {
      artists: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  async created() {
    try {
      const response = await axios.get(`https://spreadsheets.google.com/feeds/list/18kC36XlinBoxImrravjSceOXChOg4fOBW0_W0ECrWZw/1/public/full?alt=json`)
      this.artists = response.data.feed.entry
    } catch (error) {
      this.errors.push(error)
    }
  }
}
</script>