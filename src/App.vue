<template>
  <v-app>

    <v-main>
      <router-view/>
    </v-main>

    <v-avatar color="primary" size="56">123</v-avatar>
    <v-btn
        depressed
        color="primary"
      >
        Primary
      </v-btn>

  </v-app>

</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  })
}
</script>
