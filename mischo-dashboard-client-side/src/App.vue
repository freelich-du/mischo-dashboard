<template>
  <div id="app">
    <img src="./assets/logo.png">
    <el-container>
      <el-header>
        <div>
          <el-button-group>
            <el-button type="info" icon="el-icon-arrow-left" @click="backward" :disabled="!canGoBack"></el-button>
            <el-button type="info" icon="el-icon-arrow-right" @click="forward" :disabled="!canMoveForward"></el-button>
            <el-button type="info" icon="el-icon-refresh" @click="refresh"></el-button>
          </el-button-group>
          <div class="logo" @click="$router.push({path:'/'})">
            <span>Sigma</span>
          </div>
        </div>
        <div>
          <el-switch style="margin-right:20px;" v-model="autoRefresh" inactive-color="#a5a6a7" active-text="auto-refreshing">
          </el-switch>
          <a style="margin-right:20px" href='#/watch-list'>
            <i class="el-icon-bell"></i> Watch List
            <el-tag type="danger">{{watchListSize}}</el-tag>
          </a>
        </div>
      </el-header>
      <router-view style="margin-top: 60px;"/>
    </el-container>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
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

<style lang="less" scoped>
@header-bg-color: #dcdfe6;
@header-height: 60px;
.el-header {
  background-color: @header-bg-color;
  line-height: @header-height;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  left: 0;
  right: 0;
  z-index: 999;
  padding: 0;
}
.el-header > div {
  display: flex;
  align-items: center;
}
.el-button {
  background: transparent;
  color: black;
  border: none;
}
.el-button:hover {
  background: #cacdd4;
}
@logo-width: 120px;
@logo-text-size: 1.5333rem;
.logo {
  width: @logo-width;
  font-size: @logo-text-size;
  display: flex;
  align-items: center;
  cursor: pointer;
}
@breadcrumb-font-size: 1.2rem;
.el-breadcrumb {
  height: @header-height;
  line-height: @header-height;
  font-size: @breadcrumb-font-size;
}
.el-main {
  margin-top: @header-height;
}
.el-switch__core {
  background: #a5a6a7 !important;
}
</style>
