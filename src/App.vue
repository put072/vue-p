<template>
  <div id="app" class="layout">
        <Layout>
            <Header>
                <Menu mode="horizontal" theme="dark" active-name="1">
                  <div class="layout-logo"></div>
                    <div class="layout-nav">
                        <i-menu-item name="1" to="/">
                            <Icon type="ios-navigate"></Icon>
                            Home
                        </i-menu-item>
                        <i-menu-item name="2" to="/about">
                            <Icon type="ios-keypad"></Icon>
                            About
                        </i-menu-item>
                        <i-menu-item name="3" to="/result">
                            <Icon type="ios-analytics"></Icon>
                            Result
                        </i-menu-item>
                    </div>
                </Menu>
            </Header>
            <Content :style="{padding: '0 50px'}">
              <router-view/>
            </Content>
        </Layout>
        </div>
</template>

<script>
import Vue from 'vue'
import { MenuItem } from 'view-design';
Vue.component('i-menu-item', MenuItem);
  export default {
    
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
table {
  width: 100%;
}
</style>