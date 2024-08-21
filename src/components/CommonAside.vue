<template>
  <div>
    <el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
      :collapse="isCollapse" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
      <h3>菜单</h3>
      <el-menu-item v-for="item in noChildren" :key="item.name" :index="item.name">
        <i v-bind:class="`el-icon-${item.icon}`"></i>
        <span slot="title">{{ item.label }}</span>
      </el-menu-item>
      <el-submenu v-for="item in hasChildren" :key="item.label" :index="item.label">
        <template slot="title">
          <i v-bind:class="`el-icon-${item.icon}`"></i>
          <span slot="title">{{ item.label }}</span>
        </template>
        <el-menu-item v-for="hasItem in item.children" :key="hasItem.label" :index="hasItem.label">{{ hasItem.label }}
        </el-menu-item>
      </el-submenu>
    </el-menu>
  </div>

</template>


<style>
.el-menu-vertical-demo:not(.el-menu--collapse) {

  width: 200px;
  min-height: 400px;
}

.el-menu-vertical-demo {
  height: 100vh;
}

h3 {
  color: #fff;
  line-height: 60px;
  text-align: center;
}
</style>

<script>
export default {
  data() {
    return {
      isCollapse: false,
      menuData: [
        {
          path: '/',
          name: 'home',
          label: '首页',
          icon: 's-home',
        },
        {
          path: '/mall',
          name: 'mall',
          label: '商品管理',
          icon: 'video-play',
        },
        {
          path: '/user',
          name: 'user',
          label: '用户管理',
          icon: 'user',
        },
        {
          label: '其他',
          icon: 'location',
          children: [
            {
              path: '/page1',
              name: 'page1',
              label: '页面1',
              icon: 'setting',
            },
            {
              path: '/page2',
              name: 'page2',
              label: '页面2',
              icon: 'setting',
            }
          ]
        }
      ]
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  },
  computed: {

    // 有无子菜单

    // 无子菜单

    noChildren() {

      return this.menuData.filter((item) => !item.children);

    },

    // 有子菜单

    hasChildren() {

      return this.menuData.filter((item) => item.children);

    },

  },
}
</script>