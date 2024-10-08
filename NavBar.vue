<template>
  <nav class="navbar">
    <ul class="nav-list">
      <li v-for="item in navItems" :key="item.name" class="nav-item">
        <a href="#" @click="toggleDropdown(item)">{{ item.name }}</a>
        
        <!-- 下拉菜单 -->
        <ul v-if="item.dropdownVisible" class="dropdown">
          <li v-for="subItem in item.subMenu" :key="subItem.name" class="dropdown-item">
            <a :href="subItem.link">{{ subItem.name }}</a>
          </li>
        </ul>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      navItems: [
        { name: '首页', link: '/' },
        { 
          name: '产品',
          dropdownVisible: false,
          subMenu: [
            { name: '产品1', link: '/product1' },
            { name: '产品2', link: '/product2' }
          ]
        },
        { name: '关于我们', link: '/about' },
        { 
          name: '服务',
          dropdownVisible: false,
          subMenu: [
            { name: '服务1', link: '/service1' },
            { name: '服务2', link: '/service2' }
          ]
        },
        { name: '联系我们', link: '/contact' }
      ]
    }
  },
  methods: {
    toggleDropdown(item) {
      item.dropdownVisible = !item.dropdownVisible;
    }
  }
}
</script>

<style scoped>
.navbar {
  background-color: #333;
  padding: 10px;
}

.nav-list {
  list-style: none;
  display: flex;
}

.nav-item {
  margin-right: 20px;
  position: relative;
}

.nav-item a {
  color: white;
  text-decoration: none;
}

.nav-item a:hover {
  text-decoration: underline;
}

.dropdown {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: #444;
  list-style: none;
  padding: 0;
  margin: 0;
  display: block;
  min-width: 150px;
}

.dropdown-item a {
  display: block;
  padding: 10px;
  color: white;
  text-decoration: none;
}

.dropdown-item a:hover {
  background-color: #555;
}
</style>
