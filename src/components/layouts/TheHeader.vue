<template>
  <div class="navbar navbar-default topnav">
    <div class="container">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle" @click="toggleNav">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>

        <router-link to="/" class="navbar-brand">
          <span class="title">{{ logo.title }}</span>
          <img :src="logo.src" :alt="logo.title">
        </router-link>
      </div>

      <div id="top-navbar-collapse" :class="['collapse', 'navbar-collapse', { in: showCollapsedNav }]">
        <ul class="nav navbar-nav">
          <li v-for="(item, index) in navList" :class="{ active: index === activeNavIndex }">
            <a href="#" @click="changeNavIndex(index)">{{ item }}</a>
          </li>
        </ul>

        <!-- 入口组件 -->
        <div class="navbar-right">
          <!-- 搜索框 -->
          <SearchInput/>
          <TheEntry/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TheEntry from '@/components/layouts/TheEntry'
// 引入 SearchInput.vue 默认值
import SearchInput from '@/components/layouts/SearchInput'

export default {
  name: 'TheHeader',
  components: {
    TheEntry,
    // 注册 SearchInput
    SearchInput
  },
  data() {
    return {
      logo: {
        src: `${this.uploadsUrl}both/35x35`,
        title: 'Learnku Vue.js'
      },
      navList: ['社区', '头条', '问答', '教程'],
      activeNavIndex: 0,
      showCollapsedNav: false
    }
  },
  beforeCreate() {
    this.uploadsUrl = 'https://cdn.learnku.com//uploads/communities/hIZjRRdF8oVYZy69XJnT.png!/'
  },
  methods: {
    changeNavIndex(index) {
      this.activeNavIndex = index
    },
    toggleNav() {
      this.showCollapsedNav = !this.showCollapsedNav
    }
  }
}
</script>

<style scoped>
.title { display: none;}
.navbar-default .navbar-nav > .active > a { background: rgba(0,0,0,.03);}
</style>