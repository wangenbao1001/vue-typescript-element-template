<template>
  <div class="MyClientContent">
    <el-row>
      <el-col :span="4">
        <h3>Client 资源审核</h3>
      </el-col>
    </el-row>
    <el-card class="tableWrap">
      <el-table
        :data="tableData"
        style="width: 100%"
        stripe
      >
        <el-table-column
          label="ID"
          prop='id'
        ></el-table-column>
        <el-table-column
          label="服务名称"
          prop="serviceName"
        >
          <template slot-scope="scope">
            <el-button
              type="text"
              @click="handleJumpApply(scope.$index, scope.row)"
            >{{ scope.row.serviceName }}</el-button>
          </template>
        </el-table-column>
        <el-table-column
          label="申请时间"
          width="180"
        >
          <template slot-scope="scope">
            <i class="el-icon-time"></i>
            <span style="margin-left: 10px">{{ scope.row.ctime }}</span>
          </template>
        </el-table-column>
        <el-table-column
          label="状态"
          width="180"
        >
          <template>
            <el-tag
              size="medium"
              type="success"
            >状态</el-tag>
          </template>
        </el-table-column>
        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-button
              size="mini"
              type="success"
              @click="handleEdit(scope.$index, scope.row)"
            >通过</el-button>
            <el-button
              size="mini"
              type="danger"
              @click="handleEdit(scope.$index, scope.row)"
            >删除</el-button>
          </template>
        </el-table-column>
      </el-table>
      <el-pagination
        class="pagination"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage"
        :page-size="pageSize"
        layout="total, prev, pager, next, jumper"
        :total="total"
      >
      </el-pagination>
    </el-card>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
@Component({
  components: {},
})
export default class MyClient extends Vue {
  currentPage: number = 1

  total: number = 100

  pageSize: number = 20

  tableData = [
    {
      id: 23131132,
      serviceName: '服务名称',
      ctime: '2016-05-02',
      status: 0,
    },
    {
      id: 23131132,
      serviceName: '服务名称',
      ctime: '2016-05-02',
      status: 0,
    },
    {
      id: 23131132,
      serviceName: '服务名称',
      ctime: '2016-05-02',
      status: 0,
    },
  ]

  mounted() {
    this.$msg.success('aaaaa');
  }

  handleEdit(index: number, row: object) {
    console.log(index, row);
  }

  handleSizeChange(val: number) {
    console.log(`每页 ${val} 条`);
  }

  handleCurrentChange(val: number) {
    console.log(`当前页: ${val}`);
  }

  handleJumpApply() {
    this.$router.push('/clientResourceAuditDetail');
  }
}
</script>
<style lang="scss" scoped>
.MyClientContent {
  margin-top: 20px;
  .tableWrap {
    margin-top: 20px;
    .pagination {
      text-align: center;
      margin-top: 20px;
    }
  }
}
</style>
