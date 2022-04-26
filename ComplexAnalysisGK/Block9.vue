<template>
  <div class="content">
    <div class="block-wrapper">
      <div class="block1">
        <div class="block1-header">Есть ли необходимость изменений</div>
        <div class="pieLegend">
          <div class="legendText">
            <div class="pie1"></div>
            <div class="label">не было предложено изменений</div>
          </div>
          <div class="legendText">
            <div class="pie2"></div>
            <div class="label">предложили изменения</div>
          </div>
        </div>
        <div class="wrapper1">
          <div class="wrapper-legend">
            {{ 100 - roundToFixed0(parseFloat(val207) * 100) }}
          </div>
          <div class="graphs-block">
            <svg width="140px" height="140px" viewBox="0 0 42 42" class="donut">
              <circle
                class="donut-hole"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="#fff"
              ></circle>
              <circle
                class="donut-ring"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="transparent"
                stroke="#da2a0b"
                stroke-width="5"
              ></circle>
              <circle
                class="donut-segment"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="transparent"
                stroke="#1ea50d"
                stroke-width="5"
                :stroke-dasharray="
                  100 -
                  roundToFixed0(parseFloat(val207) * 100) +
                  ' ' +
                  roundToFixed0(parseFloat(val207) * 100)
                "
                stroke-dashoffset="25"
              ></circle>

              <!-- unused 10% -->
              <g class="chart-text">
                <text x="50%" y="50%" class="chart-number">
                  {{ roundToFixed0(parseFloat(val207) * 100) }}
                </text>
              </g>
            </svg>
          </div>
        </div>
      </div>
      <div class="block2">
        <div class="block2-header">
          Что необходимо изменить в первую очередь, TOP-10
        </div>
        <div class="graph-wrapper" v-for="(item, key) in sortedData" :key="key">
          <div class="block-wrapper_paragraph">
            {{ item.lable }}
          </div>
          <div class="bar">
            <div :style="sigPosition(item.percent)" class="bar-inner"></div>
            <p class="bar-wrapper_text">
              {{ roundToFixed0(parseFloat(item.percent) * 100) }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  data() {
    return {
      rowKeysPercent: [
        "Row214",
        "Row215",
        "Row216",
        "Row217",
        "Row218",
        "Row219",
        "Row220",
        "Row221",
        "Row222",
        "Row223",
        "Row224",
        "Row225",
        "Row226",
        "Row227",
        "Row228",
      ],
    };
  },
  props: [
    "val207",
    "val149",
    "val150",
    "val151",
    "val152",
    "val153",
    "val154",
    "val155",
    "val156",
    "val157",
    "matrixData",
    "slideBody",
  ],
  computed: {
    sortedData: function () {
      let rowKeysPercent = this.rowKeysPercent;

      let obj = this.slideBody["matrix"];
      let obj2 = this.matrixData;
      let objForSorting = [];
      for (let key in rowKeysPercent) {
        objForSorting.push({
          key: key,
          lable: obj[rowKeysPercent[key]]["Col1"],
          percent: obj2[rowKeysPercent[key]]["Col2"],
        });
      }
      objForSorting.sort((a, b) => (a.percent < b.percent ? 1 : -1));
      return objForSorting.slice(0, 10);
    },
  },
  methods: {
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    sigPosition: function (value) {
      if (value != 0.0) {
        return {
          width: "calc(" + parseFloat(value) * 100 * 3 + "%)",
        };
      } else {
        return {
          width: "calc(" + 0 + "%)",
        };
      }
    },
  },
};
</script>

<style scoped>
/*@import "@/assets/scss/main.scss";*/
.content {
  width: 100%;
  height: 401px;
  margin: 30px 0 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.block-wrapper {
  display: flex;
  width: 100%;
  height: 400px;
}

.graph-wrapper:hover {
  background-color: #f0eeee;
}

.graph-wrapper:active {
  background-color: #dedede;
}

.block1 {
  width: 360px;
  height: 400px;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}

.block1-header {
  margin: 33px 0 39px 26px;
  color: #000000;
  font-weight: 600;
  font-size: 14px;
  line-height: 16px;
  text-align: left;
}

.wrapper1 {
  width: 150px;
  height: 140px;
  margin: 0;
  position: relative;
}

.wrapper-legend {
  position: absolute;
  margin: 25px 0 0 99px;
  font-size: 14px;
  line-height: 14px;
  z-index: 4;
}

.graphs-block {
  z-index: 2;
}

.graphs {
  width: 40rem;
  height: 40rem;
  display: flex;
}

.chart-text {
  font: 16px/1.4em "Montserrat", Arial, sans-serif;
  fill: #000000;
  -moz-transform: translateY(0.25em);
  -ms-transform: translateY(0.25em);
  -webkit-transform: translateY(0.25em);
  transform: translateY(0.25em);
}
.chart-number {
  font-size: 0.6em;
  line-height: 1;
  text-anchor: middle;
  -moz-transform: translateY(-0.25em);
  -ms-transform: translateY(-0.25em);
  -webkit-transform: translateY(-0.25em);
  transform: translateY(-0.01em);
}

.pieLegend {
  width: 170px;
  height: 120px;
  margin: 33px 10px 0 20px;
}

.legendText {
  width: 200px;
  height: 40px;
  display: flex;
}

.pie1 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #1ea50d;
  margin: 0 6px 0 0;
}

.pie2 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #da2a0b;
  margin: 0 6px 0 0;
}

.label {
  font-size: 14px;
  line-height: 14px;
  width: 143px;
  height: 28px;
  text-align: left;
}

.block2 {
  width: 548px;
  height: 400px;
  margin: 0 0 0 120px;
  text-align: left;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.block2-header {
  margin: 33px 0 39px 0;
  color: #000000;
  font-weight: 600;
  font-size: 14px;
  line-height: 16px;
  text-align: left;
}

.block-wrapper_header {
  display: flex;
  margin: 0 0 8px 0;
  font-size: 14px;
  line-height: 16px;
  font-weight: 600;
  letter-spacing: 0.02em;
}

.bar-header {
  width: 534px;
  text-align: right;
}

.value-header {
  width: 290px;
  text-align: right;
}

.graph-wrapper {
  display: flex;
  height: 26px;
  margin: 0 0 4px 0;
  font-size: 14px;
  line-height: 16px;
}

.block-wrapper_paragraph {
  width: 410px;
  text-align: left;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 146x;
  letter-spacing: 0.02em;
  margin: auto 26px auto 2px;
}

.text-wrapper {
  margin: 0 0.1rem 0 0;
  width: 19rem;
}

.bar-wrapper {
  width: 4rem;
  height: 30rem;
  margin: 0 0 0 0.1rem;
  display: flex;
  flex-direction: column;
  padding: 0 0 0 0;
}

.bar {
  display: flex;
  flex-direction: row;
  width: 120px;
  height: 26px;
}

.bar-inner {
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #da2a0b;
}

.bar-wrapper_text {
  letter-spacing: 0.02em;
  margin: auto 0 auto 0;
}

.block-wrapper_legend {
  margin: 13px 0 0 21px;
  font-size: 10px;
  line-height: 12px;
  font-weight: 600;
  text-align: left;
}

.donut-ring:hover {
  stroke: #741807;
}

.donut-ring:active {
  stroke: #da2a0b;
}

.donut-segment:hover {
  stroke: #0f5007;
}

.donut-segment:active {
  stroke: #1ea50d;
}
</style>
 