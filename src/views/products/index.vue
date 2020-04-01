<template>
  <div class="app-container">
    <el-table
   
      :data="list"

      border
      fit
      highlight-current-row
    >
    <el-table-column align="center" label="序号" width="95">
        <template slot-scope="scope">{{ scope.$index+1 }}</template>
    </el-table-column>
    <el-table-column label="商品ID">
        <template slot-scope="scope">{{ scope.row.id }}</template>
    </el-table-column>
    <el-table-column label="商品名称" width="300%">
        <template slot-scope="scope">{{ scope.row.name }}</template>
    </el-table-column>
    <el-table-column label="商品价格">
        <template slot-scope="scope">{{ scope.row.price }}</template>
    </el-table-column>
    <el-table-column label="商品折扣">
        <template slot-scope="scope">{{ scope.row.zekou }}</template>
    </el-table-column>
    <el-table-column label="商品卖点">
        <template slot-scope="scope">{{ scope.row.info }}</template>
    </el-table-column>
    <el-table-column label="Actions" align="center" width="230" class-name="small-padding fixed-width">
        <template slot-scope="scope">
          <el-button type="primary" size="mini" @click="editp(scope.row.id)">
            编辑
          </el-button>
          <el-button size="mini" type="danger">
            删除
          </el-button>
        </template>
      </el-table-column>
      <!--<el-table-column align="center" label="ID" width="95">
        <template slot-scope="scope">{{ scope.$index }}</template>
      </el-table-column>
      <el-table-column label="Title">
        <template slot-scope="scope">{{ scope.row.title }}</template>
      </el-table-column>
      <el-table-column label="Author" width="110" align="center">
        <template slot-scope="scope">
          <span>{{ scope.row.author }}</span>
        </template>
      </el-table-column>
      <el-table-column label="Pageviews" width="110" align="center">
        <template slot-scope="scope">{{ scope.row.pageviews }}</template>
      </el-table-column>
      <el-table-column class-name="status-col" label="Status" width="110" align="center">
        <template slot-scope="scope">
          <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>
        </template>
      </el-table-column>
      <el-table-column align="center" prop="created_at" label="Display_time" width="200">
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span>{{ scope.row.display_time }}</span>
        </template>
      </el-table-column>-->
    </el-table>
  </div>
</template>

<script>
// import { getList } from '@/api/table'

export default {
  // filters: {
  //   statusFilter(status) {
  //     const statusMap = {
  //       published: 'success',
  //       draft: 'gray',
  //       deleted: 'danger'
  //     }
  //     return statusMap[status]
  //   }
  // },
  data() {
    return {
      list: [
        {
      id: 4,
      "name": "HUAWEI P30",
      "price": 4299,
      "zekou": 222,
      "info": "abcde"
    },
    {
      id: 5,
      "name": "HUAWEI P30 PRO",
      "price": 5009,
      "zekou": 222,
      "info": "abcdeF"
    },
    {
      id: 6,
      "name": "Iphone xr",
      "price": 5000,
      "zekou": 222,
      "info": "abcdefff"
    },
    {
      id: 7,
      "name": "XIAOMI 10",
      "price": 5099,
      "zekou": 222,
      "info": "abcde"
    },
    {
      id: 8,
      "name": "CHUIZI",
      "price": 4000,
      "zekou": 222,
      "info": "abcde"
    },
      ]
      // listLoading: true
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    editp(id){
      this.$router.push('/editproducts/index/'+id);
    },
    fetchData() {
      // this.listLoading = true
      // getList().then(response => {
      //   this.list = response.data.items
      //   this.listLoading = false
      // })
      this.axios({
        method:'get',
        url:'http://106.54.54.237:8000/api/h3/home/multidata'
      }).then(res=>{
        // this.list = res.data.data.banner.list
        // console.log(res.data.data.banner.list)
      })
    }
  }
};
</script>
