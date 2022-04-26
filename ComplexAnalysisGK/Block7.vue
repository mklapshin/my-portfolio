<template>
  <div class="content">
    <div class="header">
      Рейтинг параметров по оценке удовлетворенности, TOP-2*
    </div>
    <div class="block-wrapper">
      <div class="block-wrapper_paragraph"></div>
      <div class="bar-header">TOP-2</div>
      <div class="value-header">средняя оценка</div>
    </div>

    <div class="block-wrapper" v-for="(item, key) in sortedData" :key="key">
      <div class="block-wrapper_paragraph">
        {{ item.lable }}
      </div>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(item.percent)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(item.percent) * 100) }}
        </p>
      </div>
      <p class="bar-wrapper_value">
        {{ roundToFixed1(parseFloat(item.mean)) }}
      </p>
    </div>

    <div class="block-wrapper_legend">
      * сумма долей оценивших удовлетворенность на 4 и 5 по 5-балльной шкале
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  data() {
    return {
      rowKeysPercent: [
        "Row155",
        "Row156",
        "Row157",
        "Row158",
        "Row159",
        "Row160",
        "Row161",
        "Row162",
        "Row163",
      ],
      rowKeysMean: [
        "Row164",
        "Row165",
        "Row166",
        "Row167",
        "Row168",
        "Row169",
        "Row170",
        "Row171",
        "Row172",
      ],
    };
  },
  props: [
    "val149",
    "val150",
    "val151",
    "val152",
    "val153",
    "val154",
    "val155",
    "val156",
    "val157",
    "val158",
    "val159",
    "val160",
    "val161",
    "val162",
    "val163",
    "val164",
    "val165",
    "val166",
    "matrixData",
    "slideBody",
  ],
  computed: {
    sortedData: function () {
      let rowKeysPercent = this.rowKeysPercent;
      let rowKeysMean = this.rowKeysMean;
      let obj = this.slideBody["matrix"];
      let obj2 = this.matrixData;
      let objForSorting = [];
      for (let key in rowKeysPercent) {
        objForSorting.push({
          key: key,
          lable: obj[rowKeysPercent[key]]["Col1"],
          percent: obj2[rowKeysPercent[key]]["Col2"],
          mean: obj2[rowKeysMean[key]]["Col2"],
        });
      }
      objForSorting.sort((a, b) => (a.percent < b.percent ? 1 : -1));
      return objForSorting;
    },
  },
  methods: {
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
  },
};
</script>

<style scoped>
/*@import "@/assets/scss/main.scss";*/
.content {
  width: 100%;
  height: 469px;
  margin: 30px 0 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.header {
  width: 480px;
  height: 34px;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  color: #000000;
  text-align: left;
  margin: 20px 0 2px 21px;
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
  display: flex;
  flex-direction: row;
  font-weight: 600;
  width: 25%;
}

.value-header {
  width: 25%;
  margin: auto auto auto auto;
  font-weight: 600;
  display: flex;
  justify-content: center;
  align-items: center;
}

.block-wrapper {
  display: flex;
  height: 26px;
  margin: 0 0 4px 0;
  font-size: 14px;
  line-height: 16px;
}

.block-wrapper:hover {
  background-color: #f0eeee;
}

.block-wrapper:active {
  background-color: #dedede;
}

.block-wrapper_paragraph {
  width: 50%;
  text-align: left;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 14px;
  letter-spacing: 0.02em;
  margin: auto 20px auto 21px;
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
  width: 25%;
  height: 26px;
}

.bar-inner {
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #4f525f;
}

.bar-wrapper_text {
  display: block;
  letter-spacing: 0.02em;
  margin: auto 0 auto 0;
}

.bar-wrapper_value {
  width: 25%;
  margin: auto auto auto auto;
  font-weight: 600;
  display: flex;
  justify-content: center;
  align-items: center;
}

.block-wrapper_legend {
  margin: 93px 0 0 21px;
  font-size: 10px;
  line-height: 12px;
  font-weight: 600;
  text-align: left;
}
</style>
 