<template>
  <div>
    <Header></Header>
    <el-row>
      <el-col :span="24"
        ><div class="grid-content bg-purple-dark storageBox">
          <p>教学设备管理>设备报废</p>
          <div class="baikuang">
            <p class="ruku">挂失记录</p>
            <!-- Form -->
            <el-button type="text" @click="dialogFormVisible = true">
              <el-button type="danger"  class="tianjia">+新增报废</el-button>
            </el-button>
            <el-input v-model="input" class="input2" placeholder="请输入内容"></el-input>
            <el-dialog
              title="新增报废"
              :visible.sync="dialogFormVisible"
              width="1100px"
            >
              <p>
                <el-input
                  v-model="input2"
                  placeholder="请输入编码或名称"
                  class="input2"
                ></el-input>
                <span class="ruku">报废时间:</span>
                <el-date-picker
                  v-model="value2"
                  type="date"
                  placeholder="选择日期"
                  class="riqi"
                >
                </el-date-picker>
                <span>---</span>
                <el-date-picker
                  v-model="value2"
                  type="date"
                  placeholder="选择日期"
                  class="riqi zuobian"
                >
                </el-date-picker>
                <el-button type="success">查询</el-button>
              </p>
              <ScrapTabletwo></ScrapTabletwo>
              <p style="margin-top: 10px">
                <span class="ruku">挂失时间:</span>
                <el-date-picker
                  v-model="value5"
                  type="date"
                  placeholder="选择日期"
                  class="riqi"
                >
                </el-date-picker>
              </p>
              <p>
               <span class="ruku">挂失原因:</span>
                <el-input
                  type="textarea"
                  :rows="2"
                  placeholder="请输入内容"
                  v-model="textarea"
                  class="min"
                >
                </el-input>
              </p>
              <p>
                  <el-button class="juzuo" type="success" @click="dialogFormVisible = false">提交</el-button>
              </p>
            </el-dialog>

            <span class="ruku">挂失时间:</span>
            <el-date-picker
              v-model="value3"
              type="date"
              placeholder="选择日期"
              class="riqi"
            >
            </el-date-picker>
            <span>修理时间：</span>
            <el-date-picker
              v-model="value1"
              type="date"
              placeholder="选择日期"
              class="riqi zuobian"
            >
            </el-date-picker>
            <el-button type="success" class="canxun">查询</el-button>

            <el-dropdown>
              <el-button type="primary" class="orange zuothree">
                导出excel<i class="el-icon-arrow-down el-icon--right"></i>
              </el-button>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item>导入全部</el-dropdown-item>
                <el-dropdown-item>导入选中</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
            <div class="Table">
              <!-- <Table></Table> -->
              <ScrapTable></ScrapTable>
            </div>
            <div class="xiaobaikuang">
              <div id="zuo">
                <!-- Button trigger modal -->
                <button
                  type="button"
                  class="mTop anniu"
                  data-toggle="modal"
                  data-target="#myModal"
                >
                  批量删除
                </button>
              </div>
              <div id="you">
                <el-pagination
                  class="mTop"
                  background
                  layout="prev, pager, next"
                  :total="1000"
                >
                </el-pagination>
              </div>
            </div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>
<script>
import Header from "../../../../components/Header/Index";
import ScrapTable from "../../../../components/Table/scrapTable";
import ScrapTabletwo from "../../../../components/Table/scrapTabletwo";

export default {
  components: {
    Header,
    ScrapTable,
    ScrapTabletwo,
  },
  data() {
    return {
      textarea:"",
      input2: "",
      radio: "1",
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: "",
      },
      formLabelWidth: "120px",
      input: "",
      pickerOptions: {
        disabledDate(time) {
          return time.getTime() > Date.now();
        },
        shortcuts: [
          {
            text: "今天",
            onClick(picker) {
              picker.$emit("pick", new Date());
            },
          },
          {
            text: "昨天",
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit("pick", date);
            },
          },
          {
            text: "一周前",
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit("pick", date);
            },
          },
        ],
      },
      value1: "",
      value2: "",
      value3: "",
      value5: "",
    };
  },
};
</script>
<style scoped>
.min{
    margin-top: 10px;
}
.juzuo {
  margin-left: 990px;
}
.storageBox {
  background: #f4f4f6;
  padding: 20px;
  font-size: 15px;
}
.baikuang {
  background: white;
}
.ruku {
  padding: 20px;
}
.shuru {
  width: 250px;
  margin-left: 20px;
}
.tianjia {
  background: #ff495b;
  margin-left: 20px;
}
.riqi {
  width: 150px;
  margin-right: 20px;
}
.zuobian {
  margin-left: 20px;
}
.canxun {
  background: #00b698;
}
.orange {
  background: #ffa245;
  border: none;
}
.zuotwo {
  margin-left: 120px;
}
.zuothree {
  margin-left: 120px;
}
.xiaobaikuang {
  height: 50px;
}
#zuo {
  float: left;
}
#you {
  float: right;
}
.mTop {
  margin-top: 10px;
  margin-left: 20px;
}
.anniu {
  background: none;
  border: 1px solid #00b698;
  color: #00b698;
  padding: 5px;
}
.input2 {
  width: 300px;
  margin-left: 20px;
}
</style>
<style>
.el-pagination.is-background .el-pager li:not(.disabled).active{
  background: #00b698;
}
.el-pager li.active{
  background: #00b698;
}
.el-dialog__title{
  color: white;
}
.el-button--success{
  background: #00b698;
}
</style>
