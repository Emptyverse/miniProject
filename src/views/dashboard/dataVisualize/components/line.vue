<template>
  <div ref="echartsRef" class="echarts"></div>
</template>

<script setup lang="ts" name="line">
import { ref } from "vue";
import * as echarts from "echarts";
import { useEcharts } from "@/hooks/useEcharts";
const echartsRef = ref<HTMLElement>();

const initLine = (data: any) => {
  let myChart: echarts.ECharts = echarts.init(echartsRef.value as HTMLElement);
  let option: echarts.EChartsOption = {
    title: {
      text: "半年发版统计",
      textStyle: {
        color: "#000000"
      }
    },
    tooltip: {
      trigger: "axis",
      axisPointer: {
        type: "cross",
        label: {
          backgroundColor: "#6a7985"
        }
      }
    },
    legend: {
      data: ["王朝", "海洋", "腾势", "方程豹", "仰望"],
      textStyle: {
        color: "#a1a1a1"
      }
    },
    toolbox: {
      feature: {
        saveAsImage: {}
      }
    },
    grid: {
      left: "3%",
      right: "4%",
      bottom: "3%",
      containLabel: true
    },
    xAxis: [
      {
        type: "category",
        boundaryGap: false,
        data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        axisLabel: {
          color: "#a1a1a1"
        }
      }
    ],
    yAxis: [
      {
        type: "value",
        axisLabel: {
          color: "#a1a1a1"
        }
      }
    ],
    series: [
      {
        name: "王朝",
        type: "line",
        stack: "Total",
        areaStyle: {},
        emphasis: {
          focus: "series"
        },
        data: data.a
      },
      {
        name: "海洋",
        type: "line",
        stack: "Total",
        areaStyle: {},
        emphasis: {
          focus: "series"
        },
        data: data.b
      },
      {
        name: "腾势",
        type: "line",
        stack: "Total",
        areaStyle: {},
        emphasis: {
          focus: "series"
        },
        data: data.c
      },
      {
        name: "方程豹",
        type: "line",
        stack: "Total",
        areaStyle: {},
        emphasis: {
          focus: "series"
        },
        data: data.d
      },
      {
        name: "仰望",
        type: "line",
        stack: "Total",
        label: {
          show: true,
          position: "top"
        },
        areaStyle: {},
        emphasis: {
          focus: "series"
        },
        data: data.e
      }
    ]
  };
  useEcharts(myChart, option);
};
defineExpose({
  initLine
});
</script>

<style scoped lang="scss">
.echarts {
  width: 100%;
  height: 100%;
}
</style>
