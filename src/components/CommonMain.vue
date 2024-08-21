<template>
  <div>
    <!-- 栅格布局的容器 -->
    <el-row>
      <!-- 左侧内容 -->
      <el-col :span="8">
        
          <el-card id="userCard" class="box-card">
            <div class="user">
              <img src="../images/头像.webp" alt="" />
              <div class="userInfo">
                <p class="name">小美</p>
                <p class="access">管理员</p>
              </div>
            </div>
            <div class="login-Info">
              <div><span>登陆时间</span><span class="time">2024-3-26</span></div>
              <div><span>登陆地点</span><span class="time">重庆</span></div>
            </div>
          </el-card>
          <el-card class="buycard" style="margin-top: 10px;">
            <el-table :data="tableData" style="width: 100%">
              <el-table-column v-for="(val, key) in tableLable" 
              :prop="key" 
              :label="val" 
              :key="key"/>
            </el-table>
          </el-card>   
      </el-col>
      <!-- 右侧内容 -->
      <el-col :span="16" style="padding-left: 10px;">
        <div class="num">
          <el-card v-for="item in countData" :key="item.name" :body-style="{ display: 'flex', padding: '0' }">
            <i class="icon" :class="`el-icon-${item.icon}`" :style="{ background: item.color }"></i>
            <div class="detail">
              <p class="price">￥{{ item.value }}</p>
              <p class="desc">{{ item.name }}</p>
            </div>
          </el-card>
        </div>
        <el-card style="height: 230px;">
          <div id="echarts1" style="height: 230px;"></div>
        </el-card>
        <div class="graph">
          <el-card style="height: 200px;">
            <div id="echarts2" style="height: 200px;"></div>
          </el-card>
          <el-card style="height: 200px;">
            <div id="echarts3" style="height: 160px;"></div>
          </el-card>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
// 引入 echarts
import * as echarts from 'echarts';
// 引入chance
import Chance from "chance";
const chance = new Chance();
export default {
  data() {
    return {
      tableData: [
        {
          name: 'oppo',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        },
        {
          name: 'vivo',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        },
        {
          name: '苹果',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        },
        {
          name: '小米',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        },
        {
          name: '三星',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        },
        {
          name: '魅族',
          todayBuy: 100,
          monthBuy: 300,
          totalBuy: 800
        }
      ],
      tableLable: {
        name: '品牌',
        todayBuy: "今日购买",
        monthBuy: '本月购买',
        totalBuy: '总购买',
      },
      countData: [
        {
          name: "今日支付订单",
          value: 1234,
          icon: "success",
          color: "#2ec7c9",
        },
        {
          name: "今日收藏订单",
          value: 210,
          icon: "star-on",
          color: "#ffb980",
        },
        {
          name: "今日未支付订单",
          value: 1234,
          icon: "s-goods",
          color: "#5ab1ef",
        },
        {
          name: "本月支付订单",
          value: 1234,
          icon: "success",
          color: "#2ec7c9",
        },
        {
          name: "本月收藏订单",
          value: 210,
          icon: "star-on",
          color: "#ffb980",
        },
        {
          name: "本月未支付订单",
          value: 1234,
          icon: "s-goods",
          color: "#5ab1ef",
        },
      ],
    };
  },
  mounted() {
    var List = [];
    for (let i = 0; i < 7; i++) {
      List.push({
        苹果: chance.natural({ mini: 0, max: 8000 }),
        vivo: chance.natural({ mini: 0, max: 8000 }),
        oppo: chance.natural({ mini: 0, max: 8000 }),
        魅族: chance.natural({ mini: 0, max: 8000 }),
        三星: chance.natural({ mini: 0, max: 8000 }),
        小米: chance.natural({ mini: 0, max: 8000 }),
      });
    }
    var videoData = [
      {
        name: '小米',
        value: 2999,
      },
      {
        name: '苹果',
        value: 5999,
      },
      {
        name: 'vivo',
        value: 1500,
      },
      {
        name: 'oppo',
        value: 1999,
      },
      {
        name: '魅族',
        value: 2200,
      },
      {
        name: '三星',
        value: 4500,
      }
    ];
    var orderData = {
      date: ['20191001', '20191002', '20191003', '20191004', '20191005', '20191006', '20191007'],
      data: List,
    };
    var userData = [
      {
        date: '周一',
        new: 5,
        active: 200
      },
      {
        date: '周二',
        new: 10,
        active: 500
      },
      {
        date: '周三',
        new: 12,
        active: 550
      },
      {
        date: '周四',
        new: 60,
        active: 800
      },
      {
        date: '周五',
        new: 65,
        active: 550
      },
      {
        date: '周六',
        new: 53,
        active: 770
      },
      {
        date: '周日',
        new: 33,
        active: 170
      }
    ];
    const echarts1 = echarts.init(document.getElementById('echarts1'));
    // 指定图标的配置项和数据
    var echarts1option = {};
    // 处理数据xAxis
    const xAxis = Object.keys(orderData.data[0]);
    const xAxisData = {
      data: xAxis,
    };
    // 设置xAxis的值
    echarts1option.xAxis = xAxisData;
    // 设置yAxis的值
    echarts1option.yAxis = {};
    // 设置legend的值
    echarts1option.legend = {
      data: xAxis,
    };
    // 设置series值
    echarts1option.series = [];
    xAxis.forEach((key) => {
      echarts1option.series.push({
        name: key,
        data: orderData.data.map((item) => item[key]),
        type: 'line',
      });
    });
    console.log(echarts1option);
    // 使用刚指定的配置项和数据显示图标。
    echarts1.setOption(echarts1option);

    // 柱状图
    // 初始化
    const echarts2 = echarts.init(document.getElementById('echarts2'));
    // 组装options的数据
    const echarts2Option = {
      legend: {
        textStyle: {
          color: '#333'
        },
      },
      grid: {
        left: "20%",
      },
      // 提示框
      tooltip: {
        trigger: "axis",
      },
      xAxis: {
        type: "category",
        data: userData.map((item) => item.date),
        axisLine: {
          lineStyle: {
            color: "#17b3a3",
          },
        },
        axisLabel: {
          interval: 0,
          color: "#333",
        },
      },
      yAxis: [
        {
          type: "value",
          axisLine: {
            lineStyle: {
              color: "#17b3a3",
            },
          },
        }
      ],
      color: ["#2ec7c9", "#b6a2de"],
      series: [
        {
          name: "新增用户",
          data: userData.map((item) => item.new),
          type: "bar",
        },
        {
          name: "活跃用户",
          data: userData.map((item) => item.active),
          type: "bar",
        },
      ],
    };
    echarts2.setOption(echarts2Option);

    // 饼状图
    // 初始化
    const echarts3 = echarts.init(document.getElementById("echarts3"));
    // 组装options的数据
    const echarts3Option = {
      tooltip: {
        trigger: "item",
      },
      color: [
        "#0f78f4",
        "#dd536b",
        "#9462e5",
        "#a6a6a6",
        "#e1bb22",
        "#39c362",
        "#3ed1cf",
      ],
      series: [
        {
          data: videoData,
          type: "pie",
        },
      ],
    };
    echarts3.setOption(echarts3Option);
  },
};
</script>

<style>
.el .main {
  padding: 10px !important;
}

.user {
  display: flex;
  align-items: center;
  border-bottom: 1px solid #999999;
  margin-bottom: 15px;
  padding-bottom: 15px;
}

#userCard {
  height: 260px;
}

#buyCard .el-card__body {
  padding: 10px;
}

.user img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-right: 40px;
}

.login-info {
  color: #545252;
}

.time {
  margin-left: 100px;
}

.name {
  font-size: 32px;
  margin-bottom: 10px;
}

.access {
  color: #999999;
}


/* 右侧样式 */
.num {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.num .icon {
  width: 70px;
  height: 70px;
  font-size: 25px;
  color: #fff;
  text-align: center;
  line-height: 70px;
  background-color: #fff;
}

.num .detail {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 15px;
}
.num .price {
  font-size: 28px;
  margin-bottom: 8px;
  line-height: 30px;
  height: 30px;
}

.num .desc {
  font-size: 12px;
  color: #999999;
  text-align: center;
}

.num .el-card {
  width: 32%;
  margin-bottom: 10px;
}

.graph {
  display: flex;
  justify-content: space-between;
}

.graph .el-card {
  width: 48%;
  margin-top: 15px;
}

</style>