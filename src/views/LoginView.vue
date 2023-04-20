<template>
  <v-app id="inspire">
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Login form</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field name="email" label="Email" type="email" v-model="user.username"></v-text-field>
                  <v-text-field id="password" name="password" label="Password" v-model="user.password"
                    type="password"></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn @click.prevent="clickSignin()" color="primary">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      user: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    clickSignin () {
      // console.log(this.user.username, this.user.password)
      const signinApi = `${process.env.VUE_APP_API}admin/signin`
      this.$http.post(signinApi, this.user).then((res) => {
        console.log(res)
      })
    }
  }
}
</script>
