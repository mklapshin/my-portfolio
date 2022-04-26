<template>
  <div class="content">
    <div class="header">Пол</div>
    <div class="pieContainer">
      <div class="pieLegend">
        <div class="legendText">
          <div class="pie1"></div>
          <div class="label">мужской</div>
        </div>
        <div class="legendText">
          <div class="pie2"></div>
          <div class="label">женский</div>
        </div>
      </div>
      <div class="wrapper1">
        <div class="wrapper-legend">
          {{ roundToFixed0(parseFloat(val1) * 100) }}
        </div>
        <div class="wrapper-legend2">
          {{ roundToFixed0(parseFloat(val2) * 100) }}
        </div>
        <div class="graphs-block">
          <svg width="140px" height="140px" viewBox="0 0 42 42" class="donut">
            <circle
              class="donut-ring"
              cx="21"
              cy="21"
              r="7"
              fill="transparent"
              stroke="#c4c4c4"
              stroke-width="14"
            ></circle>

            <circle
              class="donut-segment2"
              cx="21"
              cy="21"
              r="7"
              fill="transparent"
              stroke="#ad1212"
              stroke-width="14"
              :stroke-dasharray="
                parseFloat(val2) * 100 + ' ' + parseFloat(val1) * 100
              "
              :stroke-dashoffset="calcDashoffset(parseFloat(val2) * 100)"
            ></circle>
            <circle
              class="donut-segment3"
              cx="21"
              cy="21"
              r="7"
              fill="transparent"
              stroke="#122692"
              stroke-width="14"
              :stroke-dasharray="
                parseFloat(val1) * 100 + ' ' + parseFloat(val2) * 100
              "
              :stroke-dashoffset="calcStroke1(parseFloat(val2) * 100)"
            ></circle>

            <!--            :stroke-dasharray="roundToFixed0(val1) + ' ' + roundToFixed0(val2)"-->

            <!-- unused 10% -->
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>



<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  props: ["val1", "val2", "slideBody"],
  methods: {
    calcDashoffset: function (string) {
      return parseFloat(string * 0.57);
    },
    calcStroke1: function (string1) {
      return parseFloat(100 - parseFloat(string1) + string1 * 0.57 * 1);
    },
    formatWithSpaces: function (string) {
      return numbFormat(string, 0, ".", " ");
    },
    roundToFixed2: function (string) {
      return numbFormat(string, 2, ".", "");
    },
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    calcStroke: function (string) {
      return parseFloat(
        100 - parseFloat(string) * 100 + parseFloat(string) * 100 * 0.56
      );
    },
  },
};
</script>

<style scoped>
/*@import "@/assets/scss/main.scss";*/
.content {
  width: 100%;
  height: 228px;
  background: #ffffff;
  border-radius: 5px;
  margin: 0 30px 30px 0;
  font-family: Inter;
}

.header {
  height: 26px;
  text-align: left;
  margin: 20px 0 0 26px;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.pieContainer {
  display: flex;
  margin: 20px 0 0 0;
}

.pieLegend {
  width: 90px;
  height: 100px;
  margin: 30px 1px 0 20px;
}

.legendText {
  width: 100px;
  height: 20px;
  display: flex;
}

.pie1 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #122692;
  margin: 0 6px 0 0;
}

.pie2 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #ad1212;
  margin: 0 6px 0 0;
}

.wrapper1 {
  width: 120px;
  height: 120px;
  margin: 0;
  position: relative;
}

.graphs-block {
  width: 120px;
  height: 120px;
}

.wrapper-legend {
  position: absolute;
  margin: 41px 0 0 41px;
  font-size: 14px;
  line-height: 16px;
  color: #ffffff;
  z-index: 4;
}

.wrapper-legend2 {
  position: absolute;
  margin: 41px 0 0 80px;
  font-size: 14px;
  line-height: 16px;
  color: #ffffff;
  z-index: 4;
}

.label {
  font-size: 14px;
  line-height: 16px;
  width: 40px;
}

.pie {
  transition: all 1s;
  position: absolute;
  width: 75px;
  height: 75px;
  border-radius: 100%;
  clip: rect(0px, 88px, 88px, 0px);
}

.graphs-block {
  transform: rotate(270deg);
  z-index: 2;
}

.donut-segment2:hover {
  stroke: #610b0b;
}

.donut-segment2:active {
  stroke: #ad1212;
}

.donut-segment3:hover {
  stroke: #09103b;
}

.donut-segment3:active {
  stroke: #122692;
}
</style>