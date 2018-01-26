<template>
<div id="app">
  <div class="header">
    <ul>
        <li><router-link to="/">首页</router-link></li>
        <li><router-link to="/upload">图片上传</router-link></li>
        <li><router-link to="/git">Git命令大全</router-link></li>
    </ul>
  </div>
  <transition>
    <router-view/>
  </transition>
</div>
  
</template>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header{height: 45px; background: #000; text-align:left;}
.header li{display: inline-block; min-width:100px; line-height: 45px; text-align: center}
.header a{text-decoration: none; display: block; width: 100%; line-height: 45px; color: #fff;}
.header .router-link-exact-active{background: #666;color: #fff;}
</style>
