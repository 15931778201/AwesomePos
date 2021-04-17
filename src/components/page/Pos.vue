<!-- pos -->
<template>
  <div class="pos">
    <div>
      <el-row>
        <el-col id="order-list" class="pos-order" :span="7">
          <el-tabs>
            <el-tab-pane label="点餐">
              <el-table
                :data="tableData"
                border
                show-summary
                style="width: 100%"
              >
                <el-table-column
                  prop="goodsName"
                  label="商品"
                ></el-table-column>
                <el-table-column
                  prop="count"
                  label="量"
                  width="50"
                ></el-table-column>
                <el-table-column
                  prop="price"
                  label="金额"
                  width="70"
                ></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template slot-scope="scope">
                    <el-button
                      type="text"
                      size="small"
                      @click="delSingleGoods(scope.row)"
                      >删除</el-button
                    >
                    <el-button
                      type="text"
                      size="small"
                      @click="addOrderList(scope.row)"
                      >增加</el-button
                    >
                  </template>
                </el-table-column>
              </el-table>
              <br />
              <div class="btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger" @click="delAllGoods">删除</el-button>
                <el-button type="success">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单"> 挂单 </el-tab-pane>
            <el-tab-pane label="外卖"> 外卖 </el-tab-pane>
          </el-tabs>
        </el-col>
        <el-col :span="17">
          <div class="often-goods">
            <div class="title">常用商品</div>
            <div class="often-goods-list">
              <ul>
                <li
                  v-for="item in oftenGoods"
                  :key="item.goodsId"
                  @click="addOrderList(item)"
                >
                  <span>{{ item.goodsName }}</span>
                  <span class="o-price"> ¥ {{ item.price }} 元</span>
                </li>
              </ul>
            </div>
          </div>
          <br />
          <div class="goods-type">
            <el-tabs>
              <el-tab-pane label="汉堡">
                <ul class="cook-list">
                  <li v-for="item in type0Goods" :key="item.goodsId">
                    <span class="foodImg">
                      <img :src="item.goodsImg" width="100%" />
                    </span>
                    <span class="foodName">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食"> 小食 </el-tab-pane>
              <el-tab-pane label="饮料"> 饮料 </el-tab-pane>
              <el-tab-pane label="套餐"> 套餐 </el-tab-pane>
            </el-tabs>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
// import axios from 'axios'
export default {
  name: 'Pos',
  data () {
    return {
      tableData: [{
        goodsName: '可口可乐',
        price: 8,
        count: 1
      }, {
        goodsName: '香辣鸡腿堡',
        price: 15,
        count: 1
      }, {
        goodsName: '爱心薯条',
        price: 8,
        count: 1
      }, {
        goodsName: '甜筒',
        price: 8,
        count: 1
      }],
      oftenGoods: [
        {
          goodsId: 1,
          goodsName: '香辣鸡腿堡',
          price: 18
        }, {
          goodsId: 2,
          goodsName: '田园鸡腿堡',
          price: 15
        }, {
          goodsId: 3,
          goodsName: '和风汉堡',
          price: 15
        }, {
          goodsId: 4,
          goodsName: '快乐全家桶',
          price: 80
        }, {
          goodsId: 5,
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 6,
          goodsName: '魔法鸡块',
          price: 20
        }, {
          goodsId: 7,
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 8,
          goodsName: '雪顶咖啡',
          price: 18
        }, {
          goodsId: 9,
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 20,
          goodsName: '香脆鸡柳',
          price: 17
        }],

      type0Goods: [
        {
          goodsId: 1,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/604_582290.jpg',
          goodsName: '香辣鸡腿堡',
          price: 20
        }, {
          goodsId: 2,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/604_582951.jpg',
          goodsName: '奥尔良鸡腿堡',
          price: 20
        }, {
          goodsId: 3,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/860_1279701.jpg',
          goodsName: '劲辣鸡腿堡',
          price: 20
        }, {
          goodsId: 4,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/1002_1661769.jpg',
          goodsName: '快乐全家桶',
          price: 100
        }, {
          goodsId: 5,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/1002_1666074.jpg',
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 6,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/1002_1657912.jpg',
          goodsName: '魔法鸡块',
          price: 12
        }, {
          goodsId: 7,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/604_583035.jpg',
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 8,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/860_1279708.jpg',
          goodsName: '鲜柠桔气泡饮',
          price: 12
        }, {
          goodsId: 9,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/1002_1661787.jpg',
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 20,
          goodsImg: 'https://img.4008823823.com.cn/kfcios/Version/604_581928.jpg',
          goodsName: '蔬菜沙拉',
          price: 15
        }
      ],
      currentGoods: {},
      totalCount: 0, // 汇总数量
      totalMoney: 0, // 汇总金额
      type1Goods: [],
      type2Goods: [],
      type3Goods: []
    }
  },
  // 生命周期 - 创建完成（访问当前this实例）
  created () {

  },
  // 生命周期 - 挂载完成（访问DOM元素）
  mounted () {
    var orderHeight = document.body.clientHeight
    document.getElementById('order-list').style.height = orderHeight + 'px'
  },
  methods: {
    addOrderList (goods) {
      this.totalCount = 0
      this.totalMoney = 0
      let isHave = false
      // 判断是否这个商品已经存在于订单列表
      for (let i = 0; i < this.tableData.length; i++) {
        if (this.tableData[i].goodsId === goods.goodsId) {
          isHave = true
        }
      }
      // 根据isHave的值判断订单列表中是否已经有此商品
      if (isHave) {
        // 存在则进行数量增加
        let arr = this.tableData.filter(i => i.goodsId === goods.goodsId)
        arr[0].count++
      } else {
        // 不存在就推入数组
        let newGoods = {
          goodsId: goods.goodsId,
          goodsName: goods.goodsName,
          price: goods.price,
          count: 1
        }
        this.tableData.push(newGoods)
      }

      // 数量价格汇总计算
      this.tableData.forEach(item => {
        this.totalCount += item.count
        this.totalMoney += item.price * item.count
      })
    },
    // 删除单个商品
    delSingleGoods (goods) {
      this.tableData = this.tableData.filter(i => i.goodsId !== goods.goodsId)
    },
    // 汇总数量和金额
    getAllMoney () {
      this.totalCount = 0
      this.totalMoney = 0
      if (this.tableData) {
        // 数量价格汇总计算
        this.tableData.forEach(item => {
          this.totalCount += item.count
          this.totalMoney += item.price * item.count
        })
      }
    },
    // 删除所有商品
    delAllGoods () {
      this.tableData = []
      this.totalCount = 0
      this.totalMoney = 0
    }
  }
}
</script>
<style scoped>
/* @import url(); 引入css类 */
.pos {
  margin: auto 5px;
}
.pos-order {
  background-color: #f9fafc;
  border-right: 1px solid #c0ccda;
  height: 100%;
}
.btn {
  margin: auto 10px;
  float: right;
}
.title {
  height: 20px;
  border-bottom: 1px solid #d3dce6;
  background-color: #f9fafc;
  padding: 10px;
}
.often-goods-list ul li {
  list-style: none;
  float: left;
  border: 1px solid #e5e9f2;
  padding: 10px;
  margin: 5px;
  background-color: #fff;
}
.o-price {
  color: #58b7ff;
}
.goods-type {
  clear: both;
  margin: auto 5px;
}
.cook-list li {
  list-style: none;
  width: 23%;
  border: 1px solid #e5e9f2;
  height: auto;
  overflow: hidden;
  background-color: #fff;
  padding: 3px;
  margin: 3px;
  float: left;
}
.cook-list li span {
  display: block;
  float: left;
}
.foodImg {
  width: 40%;
}
.foodName {
  font-size: 18px;
  padding-left: 10px;
  color: brown;
}
.foodPrice {
  font-size: 16px;
  padding-left: 10px;
  padding-top: 10px;
}
</style>
