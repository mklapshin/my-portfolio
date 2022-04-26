<template>
  <div class="content">
    <h3 class="header">Количество автомобилей</h3>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">1 автомобиль</p>
      <div class="bar">
        <div :style="sigPosition(val15)" class="bar-inner"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val15) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <div class="block-wrapper_paragraph">2 автомобиля</div>
      <div class="bar">
        <div :style="sigPosition(val16)" class="bar-inner"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val16) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <div class="block-wrapper_paragraph">3 автомобиля и более</div>
      <div class="bar">
        <div :style="sigPosition(val17)" class="bar-inner"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val17) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <div class="block-wrapper_paragraph">нет автомобиля</div>
      <div class="bar">
        <div :style="sigPosition(val18)" class="bar-inner"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val18) * 100) }}
        </p>
      </div>
    </div>
    <div :style="showLegend(parseFloat(val19) * 100)" class="header">
      Наличие закрепленного в паркинге места
    </div>
    <div class="pieContainer">
      <div :style="showLegend(parseFloat(val19) * 100)" class="pieLegend">
        <div class="legendText">
          <div class="pie1"></div>
          <div class="label">Да, есть у меня</div>
        </div>
        <div class="legendText">
          <div class="pie2"></div>
          <div class="label">Да, есть у другого члена семьи</div>
        </div>
        <div class="legendText">
          <div class="pie3"></div>
          <div class="label">Нет</div>
        </div>
        <div class="legendText">
          <div class="pie4"></div>
          <div class="label">Затрудняюсь ответить</div>
        </div>
      </div>
      <div :style="showDiagram(parseFloat(val19) * 100)" class="wrapper1">
        <div
          :style="sigPosition1(parseFloat(val19) * 100)"
          class="wrapper-legend"
        >
          {{ roundToFixed0(parseFloat(val19) * 100) }}
        </div>
        <div
          :style="
            sigPosition2(parseFloat(val19) * 100, parseFloat(val20) * 100)
          "
          class="wrapper-legend2"
        >
          {{ roundToFixed0(parseFloat(val20) * 100) }}
        </div>
        <div
          :style="sigPosition3(parseFloat(val21) * 100)"
          class="wrapper-legend3"
        >
          {{ roundToFixed0(parseFloat(val21) * 100) }}
        </div>
        <div
          :style="sigPosition4(parseFloat(val22) * 100)"
          class="wrapper-legend4"
        >
          {{ roundToFixed0(parseFloat(val22) * 100) }}
        </div>
        <div class="graphs-block">
          <svg width="140px" height="140px" viewBox="0 0 42 42" class="donut">
            <circle
              class="donut-ring"
              cx="21"
              cy="21"
              r="6.91549430918954"
              fill="transparent"
              stroke="с4с4с4"
              stroke-width="14"
            ></circle>
            <circle
              class="donut-segment2"
              cx="21"
              cy="21"
              r="6.91549430918954"
              fill="transparent"
              stroke="#4f525f"
              stroke-width="14"
              :stroke-dasharray="
                parseFloat(val19) * 100 + ' ' + (100 - parseFloat(val19) * 100)
              "
              :stroke-dashoffset="calcDashoffset(parseFloat(val19) * 100)"
            ></circle>
            <circle
              class="donut-segment3"
              cx="21"
              cy="21"
              r="6.91549430918954"
              fill="transparent"
              stroke="#937545"
              stroke-width="14"
              :stroke-dasharray="
                parseFloat(val20) * 100 + ' ' + (100 - parseFloat(val20) * 100)
              "
              :stroke-dashoffset="calcStroke1(parseFloat(val19) * 100)"
            ></circle>
            <circle
              class="donut-segment4"
              cx="21"
              cy="21"
              r="6.91549430918954"
              fill="transparent"
              stroke="#e1c7ac"
              stroke-width="14"
              :stroke-dasharray="
                parseFloat(val21) * 100 + ' ' + (100 - parseFloat(val21) * 100)
              "
              :stroke-dashoffset="
                calcStroke2(
                  parseFloat(val19) * 100 + parseFloat(val20) * 100,
                  parseFloat(val19) * 100
                )
              "
            ></circle>
            <circle
              class="donut-segment5"
              cx="21"
              cy="21"
              r="6.91549430918954"
              fill="transparent"
              stroke="#c4c4c4"
              stroke-width="14"
              :stroke-dasharray="
                roundToFixed0(parseFloat(val22) * 100) +
                ' ' +
                (100 - roundToFixed0(parseFloat(val22) * 100))
              "
              :stroke-dashoffset="
                calcStroke2(
                  roundToFixed0(
                    parseFloat(val19) * 100 +
                      parseFloat(val20) * 100 +
                      parseFloat(val21) * 100
                  ),
                  roundToFixed0(parseFloat(val19) * 100)
                )
              "
            ></circle>

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
  props: [
    "val15",
    "val16",
    "val17",
    "val18",
    "val19",
    "val20",
    "val21",
    "val22",
    "slideBody",
  ],
  methods: {
    showLegend: function (value) {
      if (value == 0) {
        return {
          display: "none",
        };
      }
    },
    showDiagram: function (value) {
      if (value == 0) {
        return {
          display: "none",
        };
      }
    },
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    calcDashoffset: function (string) {
      return parseFloat(string * 0.57);
    },
    calcStroke1: function (string1) {
      return parseFloat(100 - parseFloat(string1) + string1 * 0.57 * 1);
    },
    calcStroke2: function (string2, string1) {
      return parseFloat(
        100 - parseFloat(string2) + (string1 * 0.57 * string2) / string1
      );
    },
    sigPosition: function (value) {
      if (value != 0.0) {
        return {
          width: "calc(" + parseFloat(value) * 100 + "%)",
        };
      } else {
        return {
          width: "calc(" + 0 + "%)",
        };
      }
    },
    sigPosition1: function (value) {
      if (value == 0) {
        return {
          display: "none",
        };
      } else {
        if (value <= 40) {
          return {
            margin: "calc(" + value * 1.55 + "px)" + 0 + 0 + 65 + "px",
          };
        } else {
          return {
            margin: "calc(" + value * 0.9 + "px)" + 0 + 0 + 65 + "px",
          };
        }
      }
    },
    sigPosition2: function (value, value2) {
      if (value2 == 0) {
        return {
          display: "none",
        };
      } else {
        if (value <= 40) {
          return {
            margin: "calc(" + value * 2.4 + "px)" + 0 + 0 + 85 + "px",
          };
        } else if (value < 50 && value > 40) {
          return {
            margin: "calc(" + value * 2.1 + "px)" + 0 + 0 + 70 + "px",
          };
        } else if (value <= 61 && value > 49) {
          return {
            margin: "calc(" + value * 1.33 + "px)" + 0 + 0 + 26 + "px",
          };
        } else if (value < 65 && value > 61) {
          return {
            margin: "calc(" + value * 1.2 + "px)" + 0 + 0 + 26 + "px",
          };
        } else {
          return {
            margin: "calc(" + value * 0.74 + "px)" + 0 + 0 + 17 + "px",
          };
        }
      }
    },
    sigPosition3: function (value) {
      if (value == 0) {
        return {
          display: "none",
        };
      }
    },
    sigPosition4: function (value) {
      if (value == 0) {
        return {
          display: "none",
        };
      }
    },
  },
};
</script>

<style scoped>
/* @import "@/assets/scss/main.scss"; */
.content {
  width: calc(50% - 15px);
  height: 465px;
  margin: 0 30px 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  font-family: Inter;
}

.header {
  width: 184px;
  height: 31px;
  margin: 20px 0 15px 21px;
  text-align: left;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  color: #000000;
}

.block-wrapper {
  display: flex;
  height: 30px;
  margin: 0 0 4px 0;
}

.block-wrapper:hover {
  background-color: #f0eeee;
}

.block-wrapper:active {
  background-color: #dedede;
}

.block-wrapper:nth-child(5n) {
  display: flex;
  height: 30px;
  margin: 0 0 60px 0;
}

.block-wrapper_paragraph {
  width: 300px;
  text-align: left;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 14px;
  letter-spacing: 0.02em;
  margin: auto 130px auto 21px;
}

.text-wrapper {
  margin: 0 0.1rem 0 0;
  width: 19rem;
}

.wrapper1 {
  width: 120px;
  height: 120px;
  margin: 0;
  position: relative;
}

.wrapper-legend {
  position: absolute;
  font-size: 14px;
  line-height: 16px;
  z-index: 4;
}

.wrapper-legend2 {
  position: absolute;
  font-size: 14px;
  line-height: 16px;
  z-index: 4;
}

.wrapper-legend3 {
  margin: 39px 0 0 30px;
  position: absolute;
  font-size: 14px;
  line-height: 16px;
  z-index: 4;
}

.wrapper-legend4 {
  margin: 14px 0 0 52px;
  position: absolute;
  font-size: 14px;
  line-height: 16px;
  z-index: 4;
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
  width: 280px;
  height: 30px;
}

.bar-inner {
  width: 2.875rem;
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #937545;
}

.pieContainer {
  display: flex;
  margin: -10px 0 0 0;
}

.pieLegend {
  width: 260px;
  height: 100px;
  margin: 9px 41px 0 20px;
}

.legendText {
  width: 200px;
  height: 35px;
  display: flex;
}

.legendText:nth-child(2n) {
  width: 200px;
  height: 50px;
  display: flex;
}

.legendText:nth-child(3n) {
  width: 200px;
  height: 20px;
  display: flex;
}

.pie1 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #4f525f;
  margin: 0 6px 0 0;
}

.pie2 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #937545;
  margin: 0 6px 0 0;
}

.pie3 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #e1c7ac;
  margin: 0 6px 0 0;
}

.pie4 {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background: #c4c4c4;
  margin: 0 6px 0 0;
}

.label {
  font-size: 14px;
  line-height: 16px;
  width: 190px;
  text-align: left;
}

.pieChart {
  height: 50px;
  position: relative;
}

.pieBackground {
  position: absolute;
  width: 75px;
  height: 75px;
  border-radius: 100%;
}

.pie {
  transition: all 1s;
  position: absolute;
  width: 75px;
  height: 75px;
  border-radius: 100%;
  clip: rect(0px, 88px, 88px, 0px);
}

.innerText {
  font-size: 14px;
  line-height: 16px;
  color: #000;
  padding: 28.5px 0 0 45px;
}

.innerText2 {
  font-size: 14px;
  line-height: 16px;
  color: #000;
  padding: 0 45px 29.5px 0;
  transform: rotate(180deg);
}

.hold {
  position: absolute;
  width: 75px;
  height: 75px;
  border-radius: 100%;
  clip: rect(0px, 78px, 78px, 37px);
}

#pieSlice1 .pie {
  background-color: #c4c4c4;
  transform: rotate(0deg);
  position: relative;
}

#pieSlice2 {
  transform: rotate(180deg);
}

#pieSlice2 .pie {
  background-color: #c4c4c4;
  transform: rotate(0deg);
}

.bar-wrapper_text {
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  margin: auto 0 auto 0;
}

.graphs-block {
  transform: rotate(270deg);
  z-index: 2;
}

.donut-segment2:hover {
  stroke: #32333b;
  border: 25px solid orange;
}

.donut-segment2:active {
  stroke: #4f525f;
}

.donut-segment3:hover {
  stroke: #524127;
}

.donut-segment3:active {
  stroke: #937545;
}

.donut-segment4:hover {
  stroke: #9e8b77;
}

.donut-segment4:active {
  stroke: #e1c7ac;
}

.donut-segment5:hover {
  stroke: #777474;
}

.donut-segment5:active {
  stroke: #c4c4c4;
}
</style>
 