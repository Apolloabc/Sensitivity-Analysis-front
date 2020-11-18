<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>

  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{}
  },
  mounted(){
    this.axios({
      method: "post",
      url: "/SA-back-project/test",
      data: this.qs.stringify({
        username:'jj',
        password:'jj'
      })
    }).then((res)=>{
      console.log(res.data)
    }).catch((err)=>{
      console.log(err)
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
