<template>
  <div class="content">
    <!--    <pre>-->
    <!--      {{ top5drivers }}-->
    <!--    </pre>-->

    <div class="header">Проживание в ЖК</div>
    <div class="block-wrapper">
      <div class="block1">
        <div class="pieLegend">
          <div class="legendText">
            <div class="pie1"></div>
            <div class="label">высокая оценка<br />(9-10 по 10-б. шкале)</div>
          </div>
          <div class="legendText">
            <div class="pie2"></div>
            <div class="label">
              средняя оценка<br />
              (5-8 по 10-б. шкале)
            </div>
          </div>
          <div class="legendText">
            <div class="pie3"></div>
            <div class="label">
              низкая оценка<br />
              (1-4 по 10-б. шкале)
            </div>
          </div>
        </div>
        <div class="wrapper1">
          <div class="wrapper-legend">
            {{ roundToFixed0(parseFloat(val43) * 100) }}
          </div>
          <div
            :style="
              sigPosition1(
                roundToFixed0(parseFloat(val44) * 100),
                roundToFixed0(parseFloat(val43) * 100),
                roundToFixed0(parseFloat(val42) * 100)
              )
            "
            class="wrapper-legend-2"
          >
            {{ roundToFixed0(parseFloat(val44) * 100) }}
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
                stroke="#4f525f"
                stroke-width="5"
              ></circle>
              <circle
                class="donut-segment2"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="transparent"
                stroke="#4f525f"
                stroke-width="5"
                :stroke-dasharray="
                  parseFloat(val42) * 100 +
                  ' ' +
                  (100 - parseFloat(val42) * 100)
                "
                stroke-dashoffset="25"
              ></circle>
              <circle
                class="donut-segment3"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="transparent"
                stroke="#937545"
                stroke-width="5"
                :stroke-dasharray="
                  parseFloat(val43) * 100 +
                  ' ' +
                  (100 - parseFloat(val43) * 100)
                "
                :stroke-dashoffset="calcDashoffset(parseFloat(val42) * 100)"
              ></circle>
              <circle
                class="donut-segment4"
                cx="21"
                cy="21"
                r="15.91549430918954"
                fill="transparent"
                stroke="#e1c7a7"
                stroke-width="5"
                :stroke-dasharray="
                  parseFloat(val44) * 100 +
                  ' ' +
                  (100 - parseFloat(val44) * 100)
                "
                :stroke-dashoffset="
                  calcDashoffset1(
                    parseFloat(val42) * 100,
                    parseFloat(val43) * 100
                  )
                "
              ></circle>

              <!-- unused 10% ДОПИСАТЬ функицю вычисения stroke-dashoffset 
              и разобарться с процентами в диаграмме -->
              <g class="chart-text">
                <text x="50%" y="50%" class="chart-number">
                  {{ roundToFixed0(parseFloat(val42) * 100) }}
                </text>
              </g>
            </svg>
          </div>
        </div>
        <div class="block1-legend-1">
          средняя оценка удовлетворенности по параметру
        </div>
        <div class="block1-legend-2">
          {{ roundToFixed1(parseFloat(val45)) }}
        </div>
      </div>
      <div class="block2">
        <div class="header-green">TOP-5 драйверов</div>
        <ul class="block-list">
          <li
            class="block-list-item"
            v-for="(item, key) in saldo.top5DriversSaldo"
            :key="key"
          >
            {{ item.lableDr }}
          </li>
        </ul>
      </div>
      <div class="block2">
        <div class="header-red">TOP-5 барьеров</div>
        <ul class="block-list">
          <li
            class="block-list-item"
            v-for="(item, key) in saldo.top5BarriersSaldo"
            :key="key"
          >
            {{ item.lableBr }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  data() {
    return {
      rowsForDrivers: [
        "Row52",
        "Row53",
        "Row54",
        "Row55",
        "Row56",
        "Row57",
        "Row58",
        "Row59",
        "Row60",
        "Row61",
        "Row62",
        "Row63",
        "Row64",
        "Row65",
        "Row66",
        "Row67",
        "Row68",
        "Row69",
        "Row70",
        "Row71",
        "Row72",
        "Row73",
        "Row74",
        "Row75",
        "Row76",
        "Row77",
        "Row78",
        "Row79",
        "Row80",
        "Row81",
        "Row82",
        "Row83",
        "Row84",
        "Row85",
        "Row86",
        "Row87",
        "Row88",
        "Row89",
        "Row90",
        "Row91",
        "Row92",
        "Row93",
        "Row94",
        "Row95",
        "Row96",
        "Row97",
        "Row98",
        "Row99",
        "Row100",
        "Row101",
      ],
      rowsForBarriers: [
        "Row102",
        "Row103",
        "Row104",
        "Row105",
        "Row106",
        "Row107",
        "Row108",
        "Row109",
        "Row110",
        "Row111",
        "Row112",
        "Row113",
        "Row114",
        "Row115",
        "Row116",
        "Row117",
        "Row118",
        "Row119",
        "Row120",
        "Row121",
        "Row122",
        "Row123",
        "Row124",
        "Row125",
        "Row126",
        "Row127",
        "Row128",
        "Row129",
        "Row130",
        "Row131",
        "Row132",
        "Row133",
        "Row134",
        "Row135",
        "Row136",
        "Row137",
        "Row138",
        "Row139",
        "Row140",
        "Row141",
        "Row142",
        "Row143",
        "Row144",
        "Row145",
        "Row146",
        "Row147",
        "Row148",
        "Row149",
        "Row150",
        "Row151",
      ],
    };
  },

  props: ["val42", "val43", "val44", "val45", "matrixData", "slideBody"],
  computed: {
    saldo: function () {
      let keysListDr = this.rowsForDrivers;
      let objDrLab = this.slideBody["matrix"];
      let obDrVal = this.matrixData;

      let keysListBr = this.rowsForBarriers;
      let objBrLab = this.slideBody["matrix"];
      let obBrVal = this.matrixData;

      let objForSorting = [];

      for (let key in keysListDr) {
        objForSorting.push({
          key: key,
          lableDr: objDrLab[keysListDr[key]]["Col1"],
          valueDr: obDrVal[keysListDr[key]]["Col2"],
          lableBr: objBrLab[keysListBr[key]]["Col1"],
          valueBr: obBrVal[keysListBr[key]]["Col2"],
          saldo: this.countSaldo(
            obDrVal[keysListDr[key]]["Col2"],
            obBrVal[keysListBr[key]]["Col2"]
          ),
        });
      }
      const saldoNotNull = objForSorting.filter((val) => val.saldo !== 999);
      saldoNotNull.sort((a, b) => (a.saldo < b.saldo ? 1 : -1));
      let lengthSaldo = saldoNotNull.length;
      return {
        top5DriversSaldo: saldoNotNull.slice(0, 5),
        top5BarriersSaldo: saldoNotNull
          .slice(lengthSaldo - 5, lengthSaldo + 1)
          .reverse(),
      };
    },
    // top5drivers: function () {
    //   let keysList = this.rowsForDrivers;
    //   let obj = this.slideBody["matrix"];
    //   let obj2 = this.matrixData;
    //   let objForSorting = [];
    //   for (let key in keysList) {
    //     objForSorting.push({
    //       key: key,
    //       lable: obj[keysList[key]]["Col1"],
    //       value: obj2[keysList[key]]["Col2"],
    //     });
    //   }
    //   objForSorting.sort((a, b) => (a.value < b.value ? 1 : -1));
    //   return objForSorting.slice(0, 5);
    // },
    // top5barriers: function () {
    //   let keysList = this.rowsForBarriers;
    //   let obj = this.slideBody["matrix"];
    //   let obj2 = this.matrixData;
    //   let objForSorting = [];
    //   for (let key in keysList) {
    //     objForSorting.push({
    //       key: key,
    //       lable: obj[keysList[key]]["Col1"],
    //       value: obj2[keysList[key]]["Col2"],
    //     });
    //   }
    //   objForSorting.sort((a, b) => (a.value < b.value ? 1 : -1));
    //   return objForSorting.slice(0, 5);
    // },
  },
  methods: {
    countSaldo: function (val1, val2) {
      if (val1 === 0 && val2 === 0) {
        return 999;
      } else {
        return val1 - val2;
      }
    },
    calcDashoffset: function (string1) {
      return parseFloat(100 - parseFloat(string1) + 25);
    },
    calcDashoffset1: function (string1, string2) {
      if (parseFloat(string2) > 50) {
        return parseFloat(100 - parseFloat(string1) - parseFloat(string2) + 25);
      } else
        return parseFloat(100 - parseFloat(string1) - parseFloat(string2) + 25);
    },
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    roundToFixed1: function (string) {
      return numbFormat(string, 1, ".", "");
    },
    sigPosition: function (value) {
      if (value != 0.0) {
        return {
          width: "calc(" + parseFloat(value) * 100 * 0.93 + "%)",
        };
      } else {
        return {
          width: "calc(" + 0 + "%)",
        };
      }
    },
    sigPosition1: function (value, value1, value2) {
      if (value == 0) {
        return {
          display: "none",
        };
      } else if (value >= 14) {
        return {
          marginLeft: "calc(" + value * 3.1 + "px)",
        };
      } else if (value < 1.4) {
        return {
          marginLeft: "calc(" + value * 64 + "px)",
        };
      } else if (value1 > 52) {
        return {
          marginLeft: "calc(" + value1 * 0.7 + "px)",
        };
      } else if (value2 == 61) {
        return {
          marginLeft: "calc(" + value * 19 + "px)",
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
  height: 301px;
  margin: 30px 0 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.header {
  margin: 33px 0 2px 26px;
  color: #000000;
  font-weight: 600;
  height: 25px;
  text-align: left;
}

.block-wrapper {
  width: 100%;
  height: 180px;
  margin: 0;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.block1 {
  width: 40%;
  height: 180px;
  margin: 12px 0 0 0;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}

.wrapper1 {
  width: 150px;
  height: 140px;
  margin: 0;
  position: relative;
}

.wrapper-legend {
  position: absolute;
  margin: 54px 0 0 9.1px;
  font-size: 14px;
  line-height: 16px;
}

.wrapper-legend-2 {
  position: absolute;
  margin-top: 9px;
  margin-left: 62px;
  font-size: 14px;
  line-height: 16px;
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
  width: 200px;
  height: 120px;
  margin: 17px 17px 0 20px;
}

.legendText {
  width: 210px;
  height: 40px;
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

.label {
  font-size: 14px;
  line-height: 14px;
  width: 183px;
  height: 28px;
  text-align: left;
}

.block1-legend-1 {
  width: 180px;
  margin: 10px 69px 0 22px;
  text-align: left;
  font-size: 10px;
  line-height: 12px;
  letter-spacing: 0.02em;
  color: #1ea50d;
}

.block1-legend-2 {
  width: 30px;
  margin: 10px 45px 0 19px;
  text-align: left;
  font-size: 24px;
  line-height: 28px;
  font-weight: bold;
  letter-spacing: 0.02em;
  color: #1ea50d;
}

.block2 {
  width: 30%;
  height: 180px;
  margin: 15px 0 0 0;
  text-align: left;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.header-green {
  color: #1ea50d;
  margin: 0 0 15px 0;
  font-weight: 600;
}

.block-list {
  width: 100%;
  margin: 0 0 0 16px;
}
.block-list-item {
  margin-right: 30px;
  margin-bottom: 4px;
}

.header-red {
  color: #da2a0b;
  margin: 0 0 15px 0;
  font-weight: 600;
}

.block-wrapper_legend {
  margin: 31px 0 0 22px;
  text-align: left;
  font-size: 10px;
  line-height: 12px;
}

.donut-segment2:hover {
  stroke: #32333b;
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
</style>