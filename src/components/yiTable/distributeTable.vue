<template>
  <el-table
  
    ref="multipleTable"
    :data="tableData"
    tooltip-effect="dark"
    style="width: 100%"
    @selection-change="handleSelectionChange"
    :header-cell-style="{background:'#D7D7D7',color:'#666666'}"
  >
    <el-table-column type="selection" width="120"> </el-table-column>
    <el-table-column label="分类" width="95">
      <template slot-scope="scope">{{ scope.row.date }}</template>
    </el-table-column>
    <el-table-column prop="name" label="名称" width="70"> </el-table-column>
    <el-table-column
      prop="address"
      label="编码"
      width="80"
      show-overflow-tooltip
    >
    </el-table-column
    ><el-table-column
      prop="address"
      label="单击(元)"
      width="90"
      show-overflow-tooltip
    >
    </el-table-column
    ><el-table-column
      prop="address"
      label="数量"
      width="80"
      show-overflow-tooltip
    >
    </el-table-column
    ><el-table-column
      prop="address"
      label="规格"
      width="80"
      show-overflow-tooltip
    >
    </el-table-column
    ><el-table-column
      prop="address"
      label="存放地点"
      width="100"
      show-overflow-tooltip
    >
    </el-table-column
    ><el-table-column
      prop="address"
      label="发布时间"
      width="100"
      show-overflow-tooltip
    >
    </el-table-column>

    <el-table-column
      prop="address"
      label="领用人名字"
      width="100"
      show-overflow-tooltip
    >
    </el-table-column>
    <el-table-column
      prop="address"
      width="90"
      label="所在部门"
      show-overflow-tooltip
    >
    </el-table-column
    >
    <el-table-column
      prop="address"
      width="90"
      label="分发类型"
      show-overflow-tooltip
    >
    </el-table-column
    >
    <el-table-column prop="address" label="操作" width="200" show-overflow-tooltip>
      
    
      
      
      
      
      
      
      
      <router-link to="" tag="span">编辑</router-link>       &nbsp;
      <span>删除</span>
    </el-table-column>
  </el-table>
</template>

<script>
export default {
  data() {
    return {
      num4: 4,
      tableData: [
        {
          date: "2016-05-03",
          name: "王小虎",
          address: " 1518 弄",
        },
      ],
      multipleSelection: [],
      dialogVisible: false,
    };
  },

  methods: {

    reduce() {
      this.num4--;
      alert(this.num4);
    },
    add() {
      this.num4++;
    },
    handleChange(value) {
      console.log(value);
    },
    toggleSelection(rows) {
      if (rows) {
        rows.forEach((row) => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
  },
};
</script>
<style scoped>
::v-deep.el-table th > .cell {
    text-align: center;
}
::v-deep.el-table .cell {
    text-align: center;
}
.gaodu{
    height: 300px;
    position: relative;
}
#dingwei{
    position: absolute;
    top: -20px;
    right: 50px;
}
#zuo {
  float: left;
  margin-left: 50px;
}
#you{
    float: right;
  margin-right: 100px;

}
.text {
  height: 30px;
  width: 30px;
}
.juzhong{
    text-align: center;
}
::v-deep.el-table th > .cell {
    text-align: center;
}
::v-deep.el-table .cell {
    text-align: center;
}
</style>
<style>
    .el-button--primary{
        background: #00b698;
    }
    .el-dialog__header{
        background: #00b698;
    }
</style>
  
