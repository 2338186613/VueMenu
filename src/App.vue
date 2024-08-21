<template>
  <div id="app">
    <!--在页面中想要摆放的位置 写入标签名————尖括号+组件名即可-->
    <el-container>
      <!--在aside区域里面加入组件 -->
      <el-aside width="200px">
        <CommonAside />
      </el-aside>
      <el-container>
        <el-header>
          <CommonHeader />
        </el-header>
        <el-main>
          <CommonMain />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
//引入、注入组件
import CommonAside from './components/CommonAside.vue';
import CommonHeader from './components/CommonHeader.vue';
import CommonMain from './components/CommonMain.vue';

export default {
  name: 'App',
  components: {
    //声明引入了哪些组件
    CommonAside,
    CommonHeader,
    CommonMain,
    // Carousel,
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
}
.el-header{
  padding: 0;
}
</style>