

<template>
  <div class="foo">
hkldfkjl;skljdgk

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
      posts: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  async created() {
    try {
      const response = await axios.get(`https://spreadsheets.google.com/feeds/list/18kC36XlinBoxImrravjSceOXChOg4fOBW0_W0ECrWZw/1/public/full?alt=json`)
      this.posts = response.data.feed.entry.gs
    } catch (e) {
      this.errors.push(e)
    }
  }
}
</script>