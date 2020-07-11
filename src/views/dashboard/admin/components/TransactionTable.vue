<template>
  <el-table :data="list" style="width: 100%;padding-top: 15px;">
    <el-table-column label="订单号" min-width="50">
      <template slot-scope="scope">{{ scope.row.order_no | orderNoFilter }}</template>
    </el-table-column>
    <el-table-column label="实付额" width="195" align="center">
      <template slot-scope="scope">¥{{ scope.row.cost | toThousandFilter }}</template>
    </el-table-column>
    <el-table-column label="状态" width="100" align="center">
      <template slot-scope="{row}">
        <el-tag :type="row.status | statusFilter">{{ row.status }}</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="追踪跳链" min-width="200">
      <template slot-scope="scope">
        <span
          @click="toTrace(scope.row.trace+scope.row.order_no)"
        >{{ scope.row.trace+scope.row.order_no }}</span>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        success: 'success',
        pending: 'danger'
      }
      return statusMap[status]
    },
    orderNoFilter(str) {
      return str.substring(0, 30)
    }
  },
  data() {
    return {
      list: null
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    toTrace(url) {
      window.location.href = url
    },
    fetchData() {
      this.list = [
        {
          order_no: (Math.random() * 100000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        },
        {
          order_no: (Math.random() * 1000000).toFixed(0),
          cost: (Math.random() * 100).toFixed(2),
          status: Math.random() * 10 > 5 ? 'success' : 'pending',
          trace: 'http://igfw.ymt.io/order_robot/robot/trace?order_id='
        }
      ]
      // transactionList().then(response => {
      //   this.list = response.data.items.slice(0, 8)
      // })
    }
  }
}
</script>
