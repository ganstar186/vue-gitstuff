<template>
  <div class="home">
    <div class="container">
      <div class="row justify-content-center">
        <div class="card col-lg-4 m-3" v-for="post in listPost" :key="post.id">
          <div class="card-header">
            <h4>{{ post.name }}</h4>
          </div>
          <div class="card-body">
            <img v-bind:src="post.get_thumbnail" alt="" height="200" width="300">
            <p>{{ post.desc }}</p>
          </div>
          <div class="card-footer">
            <h5>{{ post.date_added }}</h5>
            <router-link class="btn btn-outline-primary" v-bind:to="post.get_absolute_url">Read more</router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data() {
    return {
      listPost: []
    }
  },
  components: {},
  created() {
    this.loadListPosts()
  },
  methods: {
    async loadListPosts() {
      this.listPost = await fetch(
          `${this.$store.getters.getServerUrl}/post`
      ).then(response => response.json())
      console.log(this.listPost)
    }
  }
}
</script>
