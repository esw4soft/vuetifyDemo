<template>
  <div>
    dashboard
  </div>
</template>

<script>
export default {
  created () {
    const token = document.cookie.replace(/(?:(?:^|.*;\s*)hextoken\s*=\s*([^;]*).*$)|^.*$/, '$1')
    console.log(token)
    this.$http.defaults.headers.common.Authorization = token

    const signinApi = `${process.env.VUE_APP_API}api/user/check`
    this.$http.post(signinApi, this.user).then((res) => {
      if (!res.data.success) {
        this.$router.push('login')
      }
      console.log(res)
    })
  }
}
</script>
