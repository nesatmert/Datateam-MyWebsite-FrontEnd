<template>
  <v-container>
    <v-card
      class="pa-2 mb-6 mx-auto rounded-lg"
      max-width="1000"
      color=""
      v-for="post in posts"
      :key="post._id"
    >
        <v-col cols="4">
            <v-card-title class="text-h5">
              {{post.title}}  
            </v-card-title>

            <v-card-subtitle>
                {{post.description}}
            </v-card-subtitle>

           
        </v-col>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
        posts: [],
    }),
    mounted() {
        console.log("profilkdata", this.$cookies.get('access_token'))
        this.getUserData()
        
    },
    methods: {
        getUserData() {
        return this.$axios.$get('/post/posts').then((response) => {
            this.posts=response
        console.log(response)
        })
        },
    }
  }
</script>