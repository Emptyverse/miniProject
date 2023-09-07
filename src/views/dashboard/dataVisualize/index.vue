<template>
  <div class="dataVisualize-box">
    <div class="card top-box">
      <!-- <el-tabs v-model="tabActive" class="demo-tabs">
        <el-tab-pane v-for="item in tab" :key="item.name" :label="item.label" :name="item.name"></el-tab-pane>
      </el-tabs> -->
      <div class="top-content">
        <el-row :gutter="40">
          <el-col class="mb40" :xs="24" :sm="12" :md="12" :lg="4" :xl="4">
            <div class="item-left sle">
              <span class="left-title">共计更新内容</span>
              <div class="img-box">
                <img src="./images/book-sum.png" alt="" />
              </div>
              <span class="left-number">848.132w</span>
            </div>
          </el-col>
          <el-col class="mb40" :xs="24" :sm="12" :md="12" :lg="10" :xl="10">
            <div class="item-center">
              <div class="gitee-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefOne" />
                </div>
              </div>
              <div class="gitHub-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefTwo" />
                </div>
              </div>
              <div class="today-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefThree" />
                </div>
              </div>
              <div class="yesterday-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefFour" />
                </div>
              </div>
            </div>
          </el-col>
          <el-col class="mb40" :xs="24" :sm="12" :md="12" :lg="10" :xl="10">
            <div class="item-center">
              <div class="gitee-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefFive" />
                </div>
              </div>
              <div class="gitHub-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefSix" />
                </div>
              </div>
              <div class="today-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefSeven" />
                </div>
              </div>
              <div class="yesterday-traffic traffic-box">
                <div class="book-echarts">
                  <Pie ref="pieRefEight" />
                </div>
              </div>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>
    <div class="card bottom-box">
      <div class="card bottom-box-left">
        <!-- <div class="bottom-tabs">
        <el-tabs v-model="tabActive" class="demo-tabs">
          <el-tab-pane v-for="item in tab" :key="item.name" :label="item.label" :name="item.name"></el-tab-pane>
        </el-tabs>
      </div> -->
        <div class="curve-echarts">
          <Curve ref="curveRef" />
        </div>
      </div>
      <div class="card bottom-box-right">
        <!-- <div class="bottom-tabs">
        <el-tabs v-model="tabActive" class="demo-tabs">
          <el-tab-pane v-for="item in tab" :key="item.name" :label="item.label" :name="item.name"></el-tab-pane>
        </el-tabs>
      </div> -->
        <div class="curve-echarts">
          <Line ref="lineRef"></Line>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts" name="dataVisualize">
import { ref, onMounted } from "vue";
import Pie from "./components/pie.vue";
import Curve from "./components/curve.vue";
import Line from "./components/line.vue";

// const tabActive = ref(1);
const pieRefOne = ref();
const pieRefTwo = ref();
const pieRefThree = ref();
const pieRefFour = ref();
const pieRefSix = ref();
const pieRefFive = ref();
const pieRefSeven = ref();
const pieRefEight = ref();
const curveRef = ref();
const lineRef = ref();

onMounted(() => {
  pieRefOne.value.initChart(pieData);
  pieRefTwo.value.initChart(pieData);
  pieRefThree.value.initChart(pieData);
  pieRefFour.value.initChart(pieData);
  pieRefSix.value.initChart(pieData);
  pieRefFive.value.initChart(pieData);
  pieRefEight.value.initChart(pieData);
  pieRefSeven.value.initChart(pieData);
  curveRef.value.initChart(curveData);
  lineRef.value.initLine(lineData);
});

// const tab = [
//   { label: "未来7日", name: 1 },
//   { label: "近七日", name: 2 },
//   { label: "近一月", name: 3 },
//   { label: "近三月", name: 4 },
//   { label: "近半年", name: 5 },
//   { label: "近一年", name: 6 }
// ];
const lineData = {
  a: [120, 132, 101, 134, 90, 230, 210],
  b: [220, 182, 191, 234, 290, 330, 310],
  c: [150, 232, 201, 154, 190, 330, 410],
  d: [320, 332, 301, 334, 390, 330, 320],
  e: [820, 932, 901, 934, 1290, 1330, 1320]
};
const pieData = [
  { value: 5000, name: "Gitee 访问量" },
  { value: 5000, name: "GitHub 访问量" },
  { value: 5000, name: "Git 访问量" }
];
const curveData = [
  { value: 30, spotName: "掘金" },
  { value: 90, spotName: "CSDN" },
  { value: 10, spotName: "Gitee" },
  { value: 70, spotName: "GitHub" },
  { value: 20, spotName: "知乎" },
  { value: 60, spotName: "MyBlog" },
  { value: 55, spotName: "简书" }
];
</script>

<style scoped lang="scss">
@import "./index.scss";
</style>
