<template>
  <div class="header-container">
    <div class="header-left">
      <el-button class="menu" icon="el-icon-menu" size="mini"></el-button>
      <span class="pageName">首页</span>
    </div>
    <div class="header-right">
      <el-dropdown>
        <span class="el-dropdown-link">
          <img class="userHead" src="../images/头像.webp" alt="">
        </span>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item>个人中心</el-dropdown-item>
          <el-dropdown-item>退出</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
    </div>
  </div>

  
</template>

<style>
.menu {
  margin: 0px 20px;
}
.pageName {
  color: #fff
}
.header-container {
  background-color: rgb(51, 51, 51);
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding: 4px 0px
}
.userHead {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 10px;
}
</style>