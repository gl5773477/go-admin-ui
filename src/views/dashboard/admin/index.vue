<template>
  <div class="dashboard-editor-container">
    <github-corner class="github-corner" />

    <panel-group @handleSetLineChartData="handleSetLineChartData" />

    <el-row style="background:#fff;padding:5px 5px 0;margin-bottom:32px;">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <center>下单数</center>
          <line-chart :chart-data="lineChartData" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <center>支付下单数</center>
          <line-chart :chart-data="lineChartData1" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <center>接口请求数</center>
          <line-chart :chart-data="lineChartData2" />
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <raddar-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <center>风控拦截占比</center>
          <pie-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <center>统计波动异常</center>
          <bar-chart />
        </div>
      </el-col>
    </el-row>

    <el-row>
      <el-col :xs="24" :sm="24" :lg="24">
        <!-- <div class="chart-wrapper"> -->
        <Step />
        <!-- </div> -->
      </el-col>
    </el-row>

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="8">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>最新动态</span>
          </div>
          <el-timeline>
            <el-timeline-item timestamp="2020/05/15" placement="top">
              <el-card>
                <h4>更新角色授权数据绑定</h4>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2020/05/14" placement="top">
              <el-card>
                <h4>角色名称和角色key控制唯一性；</h4>
                <h4>以及字典，参数等功能唯一性控制；</h4>
                <h4>记录总条数过滤已删除状态；</h4>
                <h4>部分已知bug的修复；</h4>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2020/4/2" placement="top">
              <el-card>
                <p>...</p>
              </el-card>
            </el-timeline-item>
          </el-timeline>
        </el-card>
      </el-col>
      <el-col :xs=" 24" :sm=" 24" :lg=" 16" style="padding-right:8px;margin-bottom:30px;">
        <div class="chart-wrapper">
          <center>异常订单列表</center>
          <transaction-table />
        </div>
      </el-col>
      <!-- <el-col :xs="24" :sm="24" :lg="12">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>视频教程</span>
          </div>
          <iframe
            id="b"
            class="b video_pc"
            src="//player.bilibili.com/player.html??cid=185732281&aid=455391649&pre_ad=0"
            scrolling="no"
            border="0"
            frameborder="no"
            framespacing="0"
            allowfullscreen="true"
            style="min-height:485px; width: 100%"
          />
        </el-card>
      </el-col>-->
    </el-row>
  </div>
</template>

<script>
import GithubCorner from '@/components/GithubCorner'
import PanelGroup from './components/PanelGroup'
import LineChart from './components/LineChart'
import RaddarChart from './components/RaddarChart'
import PieChart from './components/PieChart'
import BarChart from './components/BarChart'
import TransactionTable from './components/TransactionTable'
import Step from './components/Step'

const lineChartDataAll = {
  newVisitis: {
    expectedData: [100, 120, Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), 165],
    actualData: [12, 23, 15, 32, 8, 27, 14]
  },
  messages: {
    expectedData: [110, Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), 130, 140],
    actualData: [18, 16, 15, 10, 14, 15, 13]
  },
  purchases: {
    expectedData: [80, Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), Math.floor(Math.random() * 100), 90, 100],
    actualData: [12, 9, 10, 13, 14, 13, 13]
  },
  shoppings: {
    expectedData: [130, 140, 141, 142, 145, 150, 160],
    actualData: [120, 82, 91, 154, 162, 140, 130]
  }
}

export default {
  name: 'DashboardAdmin',
  components: {
    GithubCorner,
    PanelGroup,
    LineChart,
    RaddarChart,
    PieChart,
    BarChart,
    TransactionTable,
    Step
  },
  data() {
    return {
      lineChartData: lineChartDataAll.newVisitis,
      lineChartData1: lineChartDataAll.messages,
      lineChartData2: lineChartDataAll.purchases
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.lineChartData = lineChartDataAll[type]
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width: 1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
