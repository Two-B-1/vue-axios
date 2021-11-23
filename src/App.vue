<template>
  <div id="app">
    <img src="./assets/logo.png">

<button @click="getHandle">get请求</button>
<button @click="postHandle">post请求</button>

    <router-view/>
  </div>
</template>

<script>

import axios from 'axios'


export default {
  mounted(){
    //https://news.dingnews.net/api/hottopic/show
    this.requestGetData();
    this.requestPostData();

  },
  methods: {
    //方法一：
        requestGetData(){
      let url = "https://api2.jirengu.com/getWeather.php";
      let params = {
        city:"北京"
      }
      let options = {
        headers:{ 'Content-type': 'application/x-www-form-urlencoded'}
      }
      axios.get(
        url,
        params,
        options
      ).then(res=>{
        console.log("---",res);
      })

    },
    requestPostData(){
      let url = "https://api2.jirengu.com/getWeather.php";
      let params = {
        city:"北京"
      }
      let options = {
        headers:{ 'Content-type': 'application/x-www-form-urlencoded'}
      }
      axios.post(
        url,
        params,
        options
      ).then(res=>{
        console.log("---",res);
      })
    },
    //方法二：
      getHandle(){
        axios.get('https://api2.jirengu.com/getWeather.php',
        {
          params:{
            city:"郑州"
          },
          headers:{'Content-type': 'application/x-www-form-urlencoded'}
        }
        ).then(res=>console.log(res));
      },

      postHandle(){
        axios.post('https://api2.jirengu.com/getWeather.php',
         {
          city:"郑州"
         },
          {
           headers:{'Content-type': 'application/x-www-form-urlencoded'}
          }
        
        ).then(res=>console.log(res))
        .catch(res=>console.log(err));
      }
      
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
