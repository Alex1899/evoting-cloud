<template>
  <div id="app">
    <p><img alt="Vue logo" src="./assets/gtu-logo.png"></p>  
    <br>  
        <router-link to="/">მთავარი</router-link>&nbsp;        
        <!-- <router-link to="/castBallot">Cast Ballot</router-link>&nbsp; -->
        <!--<router-link to="/QueryAll">QueryAl</router-link> -->
        <router-link to="/queryWithQueryString">დეტალები</router-link>&nbsp;
        <!-- <router-link to="/queryByKey">query by key</router-link>&nbsp; -->
        <router-link to="/getCurrentStanding">შედეგები</router-link>&nbsp;
      
      <router-view></router-view>
    </div>
</template>

<script>

export default {
  name: 'app'  
}
</script>

<style>
body{
  background-image: url('assets/pic3.png');
  background-size: 100%;

}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.chart-wrapper {
  width: 100%;
  height: 700px;
}
.echarts {
  width: 100%;
  height: 100%;
}

#loader {
  position:fixed;
  padding-top: 250px;
}

.chart-wrapper {
  position:fixed;
  padding-left:32%;
}
</style>
