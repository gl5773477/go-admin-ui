<template>
  <div>
    <font color="red">表名字</font>
    <el-table class="tb-edit" highlight-current-row :data="tableData" style="width: 100%">
      <template v-for="item in cols">
        <el-table-column
          v-if="item.type==='normal'"
          :key="item.lable"
          :prop="item.prop"
          :label="item.label"
        />
        <el-table-column
          v-if="item.type==='sort'"
          :key="item.lable"
          :prop="item.prop"
          sortable
          :label="item.label"
        >
          <template scope="scope">
            <el-tag type="primary">{{ scope.row.type }}</el-tag>
          </template>
        </el-table-column>
      </template>
    </el-table>
    <br>
  </div>
</template>
<script>
export default {
  data() {
    return {
      cols: [
        { label: '节点编号', prop: 'node', type: 'normal' },
        { label: '名称', prop: 'name', type: 'normal' },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "名称", prop: "name", type: "normal" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "名称", prop: "name", type: "normal" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "名称", prop: "name", type: "normal" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        // { label: "类型", prop: "type", type: "sort" },
        { label: '类型', prop: 'type', type: 'sort' },
        { label: '坐标', prop: 'coordinate', type: 'normal' }
      ],
      tableData: [
        {
          node: '0051',
          name: ' 机库顶',
          type: 'UWB',
          status: '正常',
          coordinate: '12.21,34.45,34.6'
        },
        {
          node: '0061',
          name: '机库门',
          type: 'GPS',
          status: '低电',
          coordinate: '45.41,67.45,78.6'
        }
      ]
    }
  },
  methods: {
    handleCurrentChange(row, event, column) {
      console.log(row, event, column, event.currentTarget)
    },
    handleEdit(index, row) {
      console.log(index, row)
    },
    handleDelete(index, row) {
      console.log(index, row)
    }
  }
}
</script>

<style>
.tb-edit .el-input {
  display: none;
}

.tb-edit .current-row .el-input {
  display: block;
}

.tb-edit .current-row .el-input + span {
  display: none;
}
</style>
