<template>
<div>
  <el-row :gutter="20">
    <el-col :span="8">
      <el-card shadow="hover" class="mgb20" style="height:252px;">
        <div class="user-info">
          <img src="../../assets/img/img.jpg" class="user-avator" alt />
          <div class="user-info-cont">
            <div class="user-info-name">{{name}}</div>
            <div>{{role}}</div>
          </div>
        </div>
        <div class="user-info-list">
          上次登录时间：
          <span>2020-05-28</span>
        </div>
        <div class="user-info-list">
          上次登录地点：
          <span>杭州</span>
        </div>
      </el-card>
      <el-card shadow="hover" style="height:252px;">
        <div slot="header" class="clearfix">
          <span>个人信息</span>
        </div>杭州
        <el-progress :percentage="71.3" color="#42b983"></el-progress>湖州
        <el-progress :percentage="24.1" color="#f1e05a"></el-progress>温州
        <el-progress :percentage="13.7"></el-progress>金华
        <el-progress :percentage="5.9" color="#f56c6c"></el-progress>
      </el-card>
    </el-col>
    <el-col :span="16">
      <el-row :gutter="20" class="mgb20">
        <el-col :span="8">
          <el-card shadow="hover" :body-style="{padding: '0px'}">
            <div class="grid-content grid-con-1">
              <i class="el-icon-lx-people grid-con-icon"></i>
              <div class="grid-cont-right">
                <div class="grid-num">1234</div>
                <div>用户访问量</div>
              </div>
            </div>
          </el-card>
        </el-col>
        <el-col :span="8">
          <el-card shadow="hover" :body-style="{padding: '0px'}">
            <div class="grid-content grid-con-2">
              <i class="el-icon-lx-notice grid-con-icon"></i>
              <div class="grid-cont-right">
                <div class="grid-num">321</div>
                <div>系统消息</div>
              </div>
            </div>
          </el-card>
        </el-col>
        <el-col :span="8">
          <el-card shadow="hover" :body-style="{padding: '0px'}">
            <div class="grid-content grid-con-3">
              <i class="el-icon-lx-goods grid-con-icon"></i>
              <div class="grid-cont-right">
                <div class="grid-num">5000</div>
                <div>数量</div>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
      <el-card shadow="hover" style="height:403px;">
        <div slot="header" class="clearfix">
          <span>待办事项</span>
          <el-button style="float: right; padding: 3px 0" type="text">添加</el-button>
        </div>
        <el-table :show-header="false" :data="todoList" style="width:100%;">
          <el-table-column width="40">
            <template slot-scope="scope">
              <el-checkbox v-model="scope.row.status"></el-checkbox>
            </template>
          </el-table-column>
          <el-table-column>
            <template slot-scope="scope">
              <div
                class="todo-item"
                :class="{'todo-item-del': scope.row.status}"
              >{{scope.row.title}}</div>
            </template>
          </el-table-column>
          <el-table-column width="60">
            <template>
              <i class="el-icon-edit"></i>
              <i class="el-icon-delete"></i>
            </template>
          </el-table-column>
        </el-table>
      </el-card>
    </el-col>
  </el-row>
  <el-row :gutter="20">
    <el-col :span="12">
      <el-card shadow="hover">
        <schart ref="bar" class="schart" canvasId="bar" :options="options"></schart>
      </el-card>
    </el-col>
    <el-col :span="12">
      <el-card shadow="hover">
        <schart ref="line" class="schart" canvasId="line" :options="options2"></schart>
      </el-card>
    </el-col>
  </el-row>
</div>
</template>
<script>
  import Schart from 'vue-schart';
  // import bus from '../common/bus';
  export default {
    name: 'dashboard',
    data() {
      return {
        name: localStorage.getItem('ms_username'),
        todoList: [
          {
            title: '海盐县域水供水一期工程—天仙河水厂改造',
            status: false
          },
          {
            title: '永康珠坑水厂UPS主机及电池销售合同',
            status: false
          },
          {
            title: '兰溪市灵洞污水管网至城南干管工程一体化预制泵站采购项目',
            status: false
          },
          {
            title: '温州苍南（老城西片/方岩河）截污纳管工程一体化泵站',
            status: false
          },
          {
            title: '瑞安排水有限公司综保维修',
            status: true
          },
          {
            title: '长兴煤山镇污水处理厂改造提升项目',
            status: true
          }
        ],
        data: [
          {
            name: '2018/09/04',
            value: 1083
          },
          {
            name: '2018/09/05',
            value: 941
          },
          {
            name: '2018/09/06',
            value: 1139
          },
          {
            name: '2018/09/07',
            value: 816
          },
          {
            name: '2018/09/08',
            value: 327
          },
          {
            name: '2018/09/09',
            value: 228
          },
          {
            name: '2018/09/10',
            value: 1065
          }
        ],
        options: {
          type: 'bar',
          title: {
            text: '最近一周类销售图'
          },
          xRorate: 25,
          labels: ['周一', '周二', '周三', '周四', '周五'],
          datasets: [
            {
              label: '污水泵',
              data: [234, 278, 270, 190, 230]
            },
            {
              label: '电闸',
              data: [164, 178, 190, 135, 160]
            },
            {
              label: '电缆',
              data: [144, 198, 150, 235, 120]
            }
          ]
        },
        options2: {
          type: 'line',
          title: {
            text: '最近几个月各销售趋势图'
          },
          labels: ['6月', '7月', '8月', '9月', '10月'],
          datasets: [
            {
              label: '污水泵',
              data: [234, 278, 270, 190, 230]
            },
            {
              label: '电闸',
              data: [164, 178, 150, 135, 160]
            },
            {
              label: '电缆',
              data: [74, 118, 200, 235, 90]
            }
          ]
        }
      };
    },
    components: {
      Schart
    },
    computed: {
      role() {
        return this.name === 'admin' ? '超级管理员' : '普通用户';
      },mainTabs: {
        get () { return this.$store.state.tab.mainTabs },
        set (val) { this.$store.commit('updateMainTabs', val) }
      },
      mainTabsActiveName: {
        get () { return this.$store.state.tab.mainTabsActiveName },
        set (val) { this.$store.commit('updateMainTabsActiveName', val) }
      },
    },
    methods: {
      selectedTabHandle (tab) {
        tab = this.mainTabs.filter(item => item.name === tab.name)
        if (tab.length >= 1) {
          this.$router.push({ name: tab[0].name })
        }
      },
      // tabs, 删除tab
      removeTabHandle (tabName) {
        this.mainTabs = this.mainTabs.filter(item => item.name !== tabName)
        if (this.mainTabs.length >= 1) {
          // 当前选中tab被删除
          if (tabName === this.mainTabsActiveName) {
            this.$router.push({ name: this.mainTabs[this.mainTabs.length - 1].name }, () => {
              this.mainTabsActiveName = this.$route.name
            })
          }
        } else {
          this.$router.push("/")
        }
      },
      changeDate() {
        const now = new Date().getTime();
        this.data.forEach((item, index) => {
          const date = new Date(now - (6 - index) * 86400000);
          item.name = `${date.getFullYear()}/${date.getMonth() + 1}/${date.getDate()}`;
        });
      }
      // handleListener() {
      //     bus.$on('collapse', this.handleBus);
      //     // 调用renderChart方法对图表进行重新渲染
      //     window.addEventListener('resize', this.renderChart);
      // },
      // handleBus(msg) {
      //     setTimeout(() => {
      //         this.renderChart();
      //     }, 200);
      // },
      // renderChart() {
      //     this.$refs.bar.renderChart();
      //     this.$refs.line.renderChart();
      // }
    },
    // tabs, 关闭当前
    tabsCloseCurrentHandle () {
      this.removeTabHandle(this.mainTabsActiveName)
    },
    // tabs, 关闭其它
    tabsCloseOtherHandle () {
      this.mainTabs = this.mainTabs.filter(item => item.name === this.mainTabsActiveName)
    },
    // tabs, 关闭全部
    tabsCloseAllHandle () {
      this.mainTabs = []
      this.$router.push("/")
    },
    // tabs, 刷新当前
    tabsRefreshCurrentHandle () {
      var tempTabName = this.mainTabsActiveName
      this.removeTabHandle(tempTabName)
      this.$nextTick(() => {
        this.$router.push({ name: tempTabName })
      })
    },
    handleClick(row) {
      console.log(row);
    }
  };
</script>
<style scoped lang="scss">
  .main-container {
    padding: 0 5px 5px;
    position: absolute;
    top: 60px;
    left: 1px;
    right: 1px;
    bottom: 0px;
    // background: rgba(56, 5, 114, 0.5);
    .tabs {
      position: fixed;
      top: 60px;
      right: 50px;
      padding-left: 0px;
      padding-right: 2px;
      z-index: 1020;
      height: 40px;
      line-height: 40px;
      font-size: 14px;
      background: rgb(255, 253, 255);
      border-color: rgba(200, 206, 206, 0.5);
      // border-left-width: 1px;
      // border-left-style: solid;
      border-bottom-width: 1px;
      border-bottom-style: solid;
    }
    .tabs-tools {
      position: fixed;
      top: 60px;
      right: 0;
      z-index: 1020;
      height: 40px;
      // padding: 0 10px;
      font-size: 14px;
      line-height: 40px;
      cursor: pointer;
      border-color: rgba(200, 206, 206, 0.5);
      border-left-width: 1px;
      border-left-style: solid;
      border-bottom-width: 1px;
      border-bottom-style: solid;
      background: rgba(255, 255, 255, 1);
    }
    .tabs-tools:hover {
      background: rgba(200, 206, 206, 1);
    }
    .main-content {
      position: absolute;
      top: 45px;
      left: 5px;
      right: 5px;
      bottom: 5px;
      padding: 5px;
      // background: rgba(209, 212, 212, 0.5);
    }
  }
  .position-left {
    left: 200px;
  }
  .position-collapse-left {
    left: 65px;
  }

  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }

  .schart-box {
    display: inline-block;
    margin: 20px;
  }
  .schart {
    width: 600px;
    height: 400px;
  }
  .content-title {
    clear: both;
    font-weight: 400;
    line-height: 50px;
    margin: 10px 0;
    font-size: 22px;
    color: #1f2f3d;
  }
  .qiandaocss{
    font-size: 22px;
    color: #1f2f3d;
  }
  .el-row {
    margin-bottom: 20px;
  }

  .grid-content {
    display: flex;
    align-items: center;
    height: 100px;
  }

  .grid-cont-right {
    flex: 1;
    text-align: center;
    font-size: 14px;
    color: #999;
  }

  .grid-num {
    font-size: 30px;
    font-weight: bold;
  }

  .grid-con-icon {
    font-size: 50px;
    width: 100px;
    height: 100px;
    text-align: center;
    line-height: 100px;
    color: #fff;
  }

  .grid-con-1 .grid-con-icon {
    background: rgb(45, 140, 240);
  }

  .grid-con-1 .grid-num {
    color: rgb(45, 140, 240);
  }

  .grid-con-2 .grid-con-icon {
    background: rgb(100, 213, 114);
  }

  .grid-con-2 .grid-num {
    color: rgb(45, 140, 240);
  }

  .grid-con-3 .grid-con-icon {
    background: rgb(242, 94, 67);
  }

  .grid-con-3 .grid-num {
    color: rgb(242, 94, 67);
  }

  .user-info {
    display: flex;
    align-items: center;
    padding-bottom: 20px;
    border-bottom: 2px solid #ccc;
    margin-bottom: 20px;
  }

  .user-avator {
    width: 120px;
    height: 120px;
    border-radius: 50%;
  }

  .user-info-cont {
    padding-left: 50px;
    flex: 1;
    font-size: 14px;
    color: #999;
  }

  .user-info-cont div:first-child {
    font-size: 30px;
    color: #222;
  }

  .user-info-list {
    font-size: 14px;
    color: #999;
    line-height: 25px;
  }

  .user-info-list span {
    margin-left: 70px;
  }

  .mgb20 {
    margin-bottom: 20px;
  }

  .todo-item {
    font-size: 14px;
  }

  .todo-item-del {
    text-decoration: line-through;
    color: #999;
  }

  .schart {
    width: 100%;
    height: 300px;
  }
</style>
