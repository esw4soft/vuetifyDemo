
<template>
  <hello-world />
</template>

<script>
import HelloWorld from '../components/HelloWorld'

export default {

  name: 'HomeView',

  components: {
    HelloWorld
  },
  created () {
    console.log(process.env.VUE_APP_API, process.env.VUE_APP_PATH)
  }
}
</script>
