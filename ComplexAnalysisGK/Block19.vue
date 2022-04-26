<template>
  <div class="content">
    <div class="content-header">
      Дополнительные пожелания жильцов (открытые ответы)
    </div>
    <div class="content-wrapper">
      <div class="content-block-1">
        <div v-if="parseFloat(val282) != 0" class="block">
          <div class="header">
            <h3 class="header-paragraph">КОМПЛЕКС АПАРТАМЕНТОВ</h3>
          </div>
          <div class="block-wrapper">
            <p class="block-wrapper_paragraph">
              Улучшить инфраструктуру комплекса
            </p>
            <div class="bar">
              <div
                :style="sigPosition(parseFloat(val282))"
                class="bar-inner"
              ></div>
              <p class="bar-wrapper_text">
                {{ roundToFixed0(parseFloat(val282) * 100) }}
              </p>
            </div>
          </div>
        </div>
        <div v-if="parseFloat(val295) != 0" class="block">
          <div class="header">
            <h3 class="header-paragraph">
              РАЙОН, В КОТОРОМ НАХОДИТСЯ КОМПЛЕКС АПАРТАМЕНТОВ
            </h3>
          </div>
          <div class="block-wrapper">
            <p class="block-wrapper_paragraph">
              Улучшить благоустройство прилегающей территории
            </p>
            <div class="bar">
              <div
                :style="sigPosition(parseFloat(val295))"
                class="bar-inner"
              ></div>
              <p class="bar-wrapper_text">
                {{ roundToFixed0(parseFloat(val295) * 100) }}
              </p>
            </div>
          </div>
        </div>

        <div class="block">
          <div v-if="parseFloat(val297) != 0">
            <div class="header">
              <h3 class="header-paragraph">ПАРКОВКА</h3>
            </div>
            <div
              class="block-wrapper"
              v-for="(item, key) in sortedData2"
              :key="key"
            >
              <p
                v-if="parseFloat(item.percent) != 0"
                class="block-wrapper_paragraph"
              >
                {{ item.lable }}
              </p>
              <div v-if="parseFloat(item.percent) != 0" class="bar">
                <div
                  :style="sigPosition(parseFloat(item.percent))"
                  class="bar-inner"
                ></div>
                <p class="bar-wrapper_text">
                  {{ roundToFixed0(parseFloat(item.percent) * 100) }}
                </p>
              </div>
            </div>
          </div>
          <div v-if="parseFloat(val303) != 0" class="block">
            <div class="header">
              <h3 class="header-paragraph">АПАРТАМЕНТЫ</h3>
            </div>
            <div
              class="block-wrapper"
              v-for="(item, key) in sortedData3"
              :key="key"
            >
              <p
                v-if="parseFloat(item.percent) != 0"
                class="block-wrapper_paragraph"
              >
                {{ item.lable }}
              </p>
              <div v-if="parseFloat(item.percent) != 0" class="bar">
                <div
                  :style="sigPosition(parseFloat(item.percent))"
                  class="bar-inner"
                ></div>
                <p class="bar-wrapper_text">
                  {{ roundToFixed0(parseFloat(item.percent) * 100) }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="block-4">
        <div class="header">
          <h3 class="header-paragraph">УПРАВЛЯЮЩАЯ КОМПАНИЯ</h3>
        </div>
        <div class="block-wrapper" v-for="(item, key) in sortedData" :key="key">
          <p
            v-if="parseFloat(item.percent) != 0"
            class="block-wrapper_paragraph"
          >
            {{ item.lable }}
          </p>
          <div v-if="parseFloat(item.percent) != 0" class="bar">
            <div
              :style="sigPosition(parseFloat(item.percent))"
              class="bar-inner"
            ></div>
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
        "Row290",
        "Row291",
        "Row292",
        "Row293",
        "Row294",
        "Row295",
        "Row296",
        "Row297",
        "Row298",
        "Row299",
      ],
      rowKeysPercent2: ["Row303", "Row304", "Row305", "Row306", "Row307"],
      rowKeysPercent3: [
        "Row309",
        "Row310",
        "Row311",
        "Row312",
        "Row313",
        "Row314",
        "Row315",
      ],
    };
  },
  props: [
    "val282",
    "val295",
    "val297",
    "val298",
    "val299",
    "val300",
    "val301",
    "val303",
    "val304",
    "val305",
    "val306",
    "val307",
    "val308",
    "val309",
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
      return objForSorting;
    },
    sortedData2: function () {
      let rowKeysPercent2 = this.rowKeysPercent2;

      let obj = this.slideBody["matrix"];
      let obj2 = this.matrixData;
      let objForSorting = [];
      for (let key in rowKeysPercent2) {
        objForSorting.push({
          key: key,
          lable: obj[rowKeysPercent2[key]]["Col1"],
          percent: obj2[rowKeysPercent2[key]]["Col2"],
        });
      }
      objForSorting.sort((a, b) => (a.percent < b.percent ? 1 : -1));
      return objForSorting;
    },
    sortedData3: function () {
      let rowKeysPercent3 = this.rowKeysPercent3;

      let obj = this.slideBody["matrix"];
      let obj2 = this.matrixData;
      let objForSorting = [];
      for (let key in rowKeysPercent3) {
        objForSorting.push({
          key: key,
          lable: obj[rowKeysPercent3[key]]["Col1"],
          percent: obj2[rowKeysPercent3[key]]["Col2"],
        });
      }
      objForSorting.sort((a, b) => (a.percent < b.percent ? 1 : -1));
      return objForSorting;
    },
  },
  methods: {
    formatWithSpaces: function (string) {
      return numbFormat(string, 0, ".", " ");
    },
    roundToFixed1: function (string) {
      return numbFormat(string, 1, ".", "");
    },
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    calcStroke: function (string) {
      return parseFloat(
        100 - parseFloat(string) * 100 + (parseFloat(string) * 100) / 2.3
      );
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
  height: 734px;
  margin: 30px 0 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.content-header {
  margin: 20px 0 20px 21px;
  text-align: left;
  font-size: 14px;
  line-height: 16px;
  font-weight: 600;
  color: #000000;
}

.content-wrapper {
  width: 100%;
  height: 580px;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}

.content-block-1 {
  width: 50%;
  /* margin: 0 0 190px 0; */
}

.block {
  width: 420px;
  height: 100px;
}

.block:nth-child(odd) {
  margin: 0 50px 0 0;
}

.block:nth-child(2n) {
  height: 100px;
}

.block:nth-child(3n) {
  height: 280px;
}

.block-4 {
  width: 50%;
  height: 700px;
}

.header {
  width: 400px;
  height: 30px;
  display: flex;
  font-weight: bold;
  color: #000000;
  text-align: left;
  margin: 20px 0 5px 21px;
}

.header-paragraph {
  margin: 0 9px 0 0;
  width: 320px;

  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.header-bar {
  font-size: 24px;
  line-height: 28px;
  color: #937545;
}

.block-wrapper {
  display: flex;
  height: 36px;
  margin: 0 0 4px 0;
}

.block-wrapper:hover {
  background-color: #f0eeee;
}

.block-wrapper:active {
  background-color: #dedede;
}

.block-wrapper_paragraph {
  width: 308px;
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
  height: 36rem;
  margin: 0 0 0 0.1rem;
  display: flex;
  flex-direction: column;
  padding: 0 0 0 0;
}

.bar {
  display: flex;
  flex-direction: row;
  width: 62px;
  height: 36px;
}

.bar-inner {
  width: 2.875rem;
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #4f525f;
}

.bar-wrapper_text {
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  margin: auto 0 auto 0;
}

.legend-1 {
  margin: 17px 0 27px 21px;
  font-size: 14px;
  line-height: 16px;
  text-align: left;
  color: #666666;
}

.legend-2 {
  margin: 0 0 0 21px;
  text-align: left;
  font-size: 10px;
  line-height: 12px;
  color: #937545;
}
</style>
 