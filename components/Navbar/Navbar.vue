<template>
  <div class="mb-2 sm-2">
    <v-app-bar
      color="black"
      dense
      dark
    >
      <v-btn icon @click="home">
        <v-icon x-large>mdi-home</v-icon>
      </v-btn>

      <v-spacer></v-spacer>
      
    <div v-if="check == 1">
      <v-btn elevation="2" @click="login" >
        Giriş Yap
      </v-btn>
    </div>
    <div v-else>
      <v-btn elevation="2" @click="profile" >
        Profilim
      </v-btn>
      <v-btn elevation="2" @click="logout" >
        Çıkış Yap
      </v-btn>
    </div>


    </v-app-bar>
  </div>
</template>


<script>
export default ({
    data() {
        return {
            loading: false,
            check: "1",
         
        };
    },
    created() {
            if(this.$cookies.get('access_token')) {
                this.check = this.$cookies.get('access_token');
            }

    },
    methods: {
        home(){
            this.$router.push('/')
        },
        login() {
            this.$router.push('/login')
        },
        profile(){
            this.$router.push('/profile')
        },
        logout() {
            this.$cookies.removeAll()
             this.$router.push(
              {
                path: '/',
                force: true,
              },
              () => {

                window.location.reload(true)
             

              }
            )
        }
    },
})
</script>
