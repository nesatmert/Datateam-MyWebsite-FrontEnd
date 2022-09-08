<template>
  <v-container> 

    <v-card
      class="pa-2 mb-6 mx-auto rounded-lg"
      max-width="1000"
      color=""
      :key="profile._id"
    >
        <v-col cols="12" sm="10" md="10">
            <v-row 
                align="center"
                justify="space-around"
            >

<v-row  class="mb-1" justify="space-around">
                    <v-dialog
      v-model="dialog2"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="success"
          dark
          v-bind="attrs"
          v-on="on"
          text
        >
            <v-icon left>
                mdi-pencil
            </v-icon>
          Düzenle
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">Profil Düzenle</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
                <v-col cols="12" sm="6" md="6">
                
                    <v-text-field
                    v-model="adcity"
                    label="Şehir"
                    required
                    ></v-text-field>
              
                </v-col>

                <v-col cols="12" sm="6" md="6">
                    <v-text-field
                        v-model="adgithub"
                        label="github"
                        required
                        :rules="emailRules"
                    ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                    <v-text-field
                        v-model="adlinkedin"
                        label="Linkedin"
                        required
                        :rules="emailRules"
                    ></v-text-field>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                    <v-text-field
                        v-model="adwebsite"
                        label="Website"
                        required
                        :rules="emailRules"
                    ></v-text-field>
                </v-col>
            <v-col cols="12" md="12">
              <v-textarea
                v-model="adbiog"
                outlined
                name="input-7-4"
                label="Biografi"
              ></v-textarea>
            </v-col>
            </v-row>
         
          </v-container>
        </v-card-text>
        <v-spacer></v-spacer>
        <v-card-actions>
          
          <v-btn
            color="blue darken-1"
            text
            @click="dialog2 = false"
          >
            Kapat
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="editMyUser"
          >
            Kaydet
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    </v-row>  








                <v-row  class="mb-1" justify="end">
                    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="success"
          dark
          v-bind="attrs"
          v-on="on"
        >
            <v-icon left>
                mdi-pencil
            </v-icon>
          Post Oluştur
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="text-h5">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
                 <v-col cols="12" sm="6" md="12">
              <v-text-field
                v-model="adtitle"
                label="Başlık"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12" md="12">
              <v-textarea
                v-model="addescription"
                outlined
                name="input-7-4"
                label="Postun içeriği"
              ></v-textarea>
            </v-col>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Kapat
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="createPost"
          >
            Kaydet
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    </v-row>  
    </v-row>

            <v-list-item-title class="title">
                <v-icon class="pa-1" size="20">mdi-account-badge</v-icon>
           
              {{ profile.user_name }}
            </v-list-item-title>

            <v-list-item-subtitle><v-icon class="pa-1" size="20">mdi-email</v-icon> {{ profile.mail}}</v-list-item-subtitle>
            <v-list-item-subtitle>
              <v-icon class="pa-1" size="20">mdi-shield-home</v-icon>
              {{ profile.city }}
            </v-list-item-subtitle>
                <v-list-item-subtitle>
                  <v-icon class="pa-1" size="20">mdi-github</v-icon>
                  {{ profile.github }}</v-list-item-subtitle
                >
                <v-list-item-subtitle>
                  <v-icon class="pa-1" size="20">mdi-linkedin</v-icon>
                  {{ profile.linkedin }}</v-list-item-subtitle
                >
                <v-list-item-subtitle>
                  <v-icon class="pa-1" size="20">mdi-web</v-icon>
                  {{ profile.website }}</v-list-item-subtitle
                >
                <v-list-item-subtitle>
                    <v-icon class="pa-1" size="20">mdi-post</v-icon>
                  {{ profile.biography }}
                </v-list-item-subtitle>
              </v-col>
             

    </v-card>
    <v-card
      class="pa-2 mb-10 mx-auto rounded-lg"
      max-width="1000"
      color=""
    >
        <h1>Postlarım</h1>
    <v-card
        class="pa-2 mb-6 mx-auto rounded-lg"
        max-width="1000"
        color=""
        v-for="(post, postid) in posts"
        :key="postid"
        >
            <v-col cols="4">
                <v-row justify="end">
                            <v-btn
                
                 text
                 v-on:click="deletePost(post)"
                
                >
                    <v-icon left>
                        mdi-delete
                    </v-icon>
                </v-btn>
                </v-row>
        
                <v-card-title class="text-h5">
                {{post.title}}  
                </v-card-title>

                <v-card-subtitle>
                    {{post.description}}
                </v-card-subtitle>

            
            </v-col>
        </v-card>
</v-card>

</v-container>





</template>

<script>
  export default {
    data: () => ({
        dialog: false,
        dialog2:false,
        adcity:null,
        adgithub:"",
        adlinkedin:null,
        adwebsite:null,
        adbiog:null,
        adtitle: null,
        addescription: null,
        profile: [],
        posts:[],
        user:"",
        token:"",
        emailRules: [
          (v) => !!v || 'E-posta alanı boş bırakılamaz',
          (v) => /.+.+\.com+/.test(v) || 'Geçerli bir e mail girin',
        ],
    }),
    created() {
        this.user = this.$cookies.get('user_id')
        this.token = this.$cookies.get('access_token')
        this.getUserData()
        this.getUserPost()
        
    },
    methods: {
        async getUserData() {
        return await this.$axios.get('/user/myuser/'+ this.user,{
            headers: {
            access_token: this.token
            }
        }).then((response) => {
                    this.profile=response.data
                })
                },

            
        async getUserPost() {
        return await this.$axios.get('/user/post/'+ this.user,{
            headers: {
            access_token: this.token
            }
            }).then((response) => {
                console.log(response)
            this.posts=response.data
        })
        },

    async createPost() {
      let postSchema = {
        title: this.adtitle,
        description: this.addescription,
      }
      await this.$axios
        .$post('/post/create',postSchema,{
            
            headers: {
                 Authorization: `Bearer ${this.token}`, 
            },
        })
        .then((response) => {
            
          console.log(response)

          this.dialog = false
        window.location.reload(true)

        })
        .catch((error) => {
          console.log(error)
        })
    },

    async editMyUser(){
        let editUser = {
            biography : this.adbiog,
            city : this.adcity,
            github : this.adgithub,
            linkedin : this.adlinkedin,
            website : this.adwebsite,
        }
        console.log(editUser)
        await this.$axios
        .$put('/user/edit/'+ this.user ,editUser,{
            headers: {
                 Authorization: `Bearer ${this.token}`, 
            },
        })
        .then((response) => {
          console.log(response)

          this.dialog2 = false
            window.location.reload(true)
        })
        .catch((error) => {
          console.log(error)
        })

    },

    async deletePost(data){
        console.log(data._id)
         await this.$axios
        .$delete('/user/post/delete/'+ data._id ,{
            headers: {
                 Authorization: `Bearer ${this.token}`, 
            },
        })
        .then((response) => {
            console.log(response)
            window.location.reload(true)
        })
        .catch((error) => {
          console.log(error)
        })
    },

    }
    }
        

</script>