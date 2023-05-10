<template>
  <div>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>
      <v-toolbar-title>Desktop Menu</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-toolbar-items>
        <v-btn v-for="item in nav" :key="item.icon" :to="{name: item.route}" :title="item.title" text>{{ item.text }}</v-btn>
        <v-btn @click.prevent="logout" text>登出</v-btn>
      </v-toolbar-items>

      <!-- <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn> -->
    </v-app-bar>

    <v-app-bar app dark color="blue-grey darken-3" class="hidden-sm-and-up">
      <v-toolbar-title>Mobile Menu</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-dialog v-model="dialog" fullscreen hide-overlay transition="dialog-bottom-transition">

          <template v-slot:activator="{ on, attrs }">
            <v-btn v-on="on" v-bind="attrs">
              <v-icon>mdi-menu</v-icon>
            </v-btn>
          </template>

        <v-card>
          <v-toolbar text color="blue-grey darken-3">
            <v-toolbar-title class="white--text">Mobile Menu</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon @click.native="dialog = false">
              <v-icon class="white--text">mdi-close</v-icon>
            </v-btn>
          </v-toolbar>

          <!-- <v-list>
            <v-list-tile v-for="(item, index) in nav" :key="index" to="#">
              <v-list-tile-action>
                <v-icon v-if="item.icon">{{ item.icon }}</v-icon>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title :title="item.title">{{ item.text }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list> -->

          <v-list dense>
            <v-list-item-group
              color="primary"
            >
              <v-list-item
                v-for="(item, index) in nav"
                :key="index" to="#"
              >
                <v-list-item-icon>
                  <v-icon v-if="item.icon">{{ item.icon }}</v-icon>
                </v-list-item-icon>
                <v-list-item-content>
                  <v-list-item-title :title="item.title">{{ item.text }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-item-group>
          </v-list>
        </v-card>
      </v-dialog>

    </v-app-bar>
  </div>
</template>

<script>
export default {
  data () {
    return {
      dialog: false,
      nav: [
        {
          icon: 'mdi-home-flood',
          text: 'home',
          title: 'Back to Home page',
          active: true,
          route: 'home'
        },
        {
          icon: 'mdi-information-outline',
          text: 'about',
          title: 'About this demo',
          active: false,
          route: 'about'
        },
        {
          icon: 'mdi-view-dashboard',
          text: 'dashboard',
          title: 'Some stuff that needs doing',
          active: false,
          route: 'dashboard'
        },
        {
          icon: 'mdi-login',
          text: 'login',
          title: 'Our Contact info',
          active: false,
          route: 'login'
        }
      ]
    }
  },
  methods: {
    logout () {
      // console.log(this.user.username, this.user.password)
      const signinApi = `${process.env.VUE_APP_API}logout`
      this.$http.post(signinApi, this.user)
        .then((res) => {
          if (res.data.success) {
            console.log(res)
            this.$router.push('/login')
          }
        })
    }
  }
}
</script>
