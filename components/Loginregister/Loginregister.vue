<template>
  <v-container class="text-center">
    <v-progress-circular
      v-if="loading"
      :size="70"
      :width="7"
      color="#c1b3fd"
      indeterminate
    ></v-progress-circular>    
    <v-row  v-if="!loading" class="text-center">
      <v-col cols="12" sm="12" class="text-center  mt-10">
        <v-card class="elevation-0 mt-10">
          <v-window v-model="onboarding" class="blue accent-3 text-center">
            <v-window-item :value="1">
              <v-row cols="12">
                <v-col cols="12" md="7" class="light-blue accent-2 text-center">
                  <v-card-text class="mt-10">
                    <div class="white--text text-center bold text-3xl">
                      Hesabınıza giriş yapın.
                    </div>
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                        <v-text-field
                          v-model="email"
                          label="Email"
                          :rules="emailRules"
                          required
                          outlined
                          dense
                          color="white"
                          autocomplete="false"
                          class="mt-16"
                        />
                        <v-text-field
                          v-model="password"
                          label="Şifre"
                          required
                          :type="showPassword ? 'text' : 'password'"
                          :append-icon="
                            showPassword ? 'mdi-eye' : 'mdi-eye-off'
                          "
                          @click:append="showPassword = !showPassword"
                          outlined
                          dense
                          color="white"
                          autocomplete="false"
                        />



                        <v-btn color="blue" dark block @click="loginUser"
                          >Giriş</v-btn
                        >
                        <v-alert
                          v-if="alert"
                          class="mt-2"
                          dense
                          outlined
                          type="error"
                        >
                          Lütfen kullanıcı adınızı yada şifrenizi kontrol edin.
                        </v-alert>

                        <div class="text-center white--text mt-4 mb-3">
                          veya şununla giriş yapın
                        </div>
                        <div
                          class="
                            d-flex
                            justify-space-between
                            align-center
                            mx-10
                            mb-20
                          "
                        >
                       
                          <v-btn depressed outlined color="grey">
                            <v-icon color="blue">mdi-facebook</v-icon>
                          </v-btn>
                             <v-btn depressed outlined color="grey">
                            <v-icon color="red ">mdi-google</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey" class="">
                            <v-icon color="light-blue lighten-3"
                              >mdi-twitter</v-icon
                            >
                          </v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-col>

                <v-col
                  cols="12"
                  md="5"
                  class="
                    caption
                    blue
                    pa-4
                    text-center
                    secondary
                    text-no-wrap
                    rounded-l-xl
                  "
                >
                  <div style="text-align: center; padding: 180px 0">
                    <v-card-text class="white--text">
                      <div class="text-center text-lg-h6">
                        Hesabınız yok mu?
                      </div>
                      <div class="text-center">
                        Hemen yeni bir hesap oluşturun.<br />
                      </div>
                    </v-card-text>
                    <div class="text-center">
                      <v-btn tile outlined dark @click="next">Kayıt Ol</v-btn>
                    </div>
                  </div>
                </v-col>
              </v-row>
            </v-window-item>

            <v-window-item :value="2">
              <v-row>
                <v-col
                  cols="12"
                  md="5"
                  class="
                    blue
                    pa-4
                    text-center
                    secondary
                    text-no-wrap
                    rounded-r-xl
                  "
                >
                  <div style="text-align: center; padding: 180px 0">
                    <v-card-text class="white--text">
                      <div class="text-center text-lg-h6">Hesabın varmı?</div>
                      <div class="text-center">
                        Hesabınla giriş yap <br />
                      </div>
                    </v-card-text>
                    <div class="text-center">
                      <v-btn tile outlined dark @click="prev">Giriş Yap</v-btn>
                    </div>
                  </div>
                </v-col>

                <v-col cols="12" md="7" class="light-blue accent-2">
                  <v-card-text class="mt-12">
                    <div class="white--text text-center bold text-3xl">
                      Kayıt Ol
                    </div>
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                        <v-row>
                          <v-col cols="12" sm="12">
                            <v-text-field
                              v-model="rname"
                              label="İsim Soyisim"
                              required
                              outlined
                              dense
                              color="white"
                              autocomplete="false"
                              class="mt-4"
                            />
                          </v-col>
                          </v-row>
                          <v-text-field
                            v-model="remail"
                            label="Email"
                            :rules="emailRules"
                            required
                            outlined
                            dense
                            color="white"
                            autocomplete="false"
                          />
                          <v-text-field
                            v-model="rpassword"
                            label="Şifre"
                            required
                            outlined
                            dense
                            color="white"
                            autocomplete="false"
                            type="password"
                          />
                          <v-row>
                        </v-row>
                        <v-btn color="blue" dark block tile @click="userReg"
                          >Kayıt Ol</v-btn
                        >
                        <v-alert
                          v-if="regalert"
                          class="mt-2"
                          dense
                          outlined
                          type="error"
                        >
                          Kayıt başarısız.<br>Lütfen bilgileri kontol edip, tekrar deneyin.
                        </v-alert>
                        <div class="text-center white--text mt-4 mb-3">
                          Yada kayıt olmak için
                        </div>

                        <div
                          class="
                            d-flex
                            justify-space-between
                            align-center
                            mx-10
                            mb-14
                          "
                        >
                          <v-btn depressed outlined color="grey">
                            <v-icon color="blue">mdi-facebook</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey">
                            <v-icon color="red ">mdi-google</v-icon>
                          </v-btn>
                          <v-btn depressed outlined color="grey" class="">
                            <v-icon color="light-blue lighten-3"
                              >mdi-twitter</v-icon
                            >
                          </v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-col>
              </v-row>
            </v-window-item>
          </v-window>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Cookie from "js-cookie";
export default {
  data: () => ({
    length: 3,
    onboarding: 1,
    showPassword: false,
    email: null,
    password: null,
    remail: null,
    rpassword: null,
    ropti: null,
    rname: null,
    alert: false,
    regalert: false,
    loading:false,
    emailRules: [
      (v) => !!v || 'E-posta alanı boş bırakılamaz',
      (v) => /.+@.+\..+/.test(v) || 'Geçerli bir e mail girin',
    ],
  }),

  methods: {
    next() {
      this.onboarding =
        this.onboarding + 1 === this.length ? 0 : this.onboarding + 1
    },
    prev() {
      this.onboarding =
        this.onboarding - 1 < 0 ? this.length - 1 : this.onboarding - 1
    },

    async loginUser() {
      let MailPW = {
        mail: this.email,
        password: this.password,
      }

      return await this.$axios
        .$post('/user/login', MailPW ,{common: {
      'Accept': 'application/json, text/plain, */*'
    }},)
        .then((response) => {
            this.loading=false
            console.log("giriş başarılı",response)
          this.alert = false




        if(response){
          
          this.$cookies.set('user_id', response._id, {
          path: '/',
          maxAge: 60 * 60 * 24 * 7
        });
          this.$cookies.set('access_token', response.access_token, {
          path: '/',
          maxAge: 60 * 60 * 24 * 7
        });
           
        }
         
           this.$router.push(
              {
                path: '/profile',
                force: true,
              },
              () => {

                window.location.reload(true)
                this.loading=false

              }
            )
        })
        .catch((error) => {
          if (error.response.status === 400) {
            this.$router.push('/')
            this.alert = true
          }
        })
    },

    async userReg() {
      let Reg = {
        
        user_name: this.rname,
        mail: this.remail,
        password: this.rpassword,
      }
        await this.$axios
          .$post('/user/register', Reg)
          .then((response) =>{
console.log(response)
            window.location.reload(true)
          } 
          ).catch((error) => {
          if (error.response.status === 400) {
            this.$router.push('/login')
            this.regalert = true
          }
        })
      this.$router.push('/login')
    },
  },
}
</script>

<style scoped>
.v-application .light-blue.accent-2{
background-color: #3a3a3a !important;

}
.v-application .blue {
  background-color: #272727 !important;
}
.mdi-twitter::before {
    color: darkblue;
}
.mdi-facebook::before {
    color: darkblue;
}
</style>>
