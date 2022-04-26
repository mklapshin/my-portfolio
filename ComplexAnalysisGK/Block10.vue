<template>
  <div class="content">
    <div class="header">
      <h3 class="header-paragraph">
        Организация системы охраны и безопасности территории
      </h3>
      <h3 class="header-bar">{{ roundToFixed1(parseFloat(val223)) }} &#42;</h3>
    </div>
    <div class="block-wrapper" v-for="(item, key) in sortedData" :key="key">
      <p class="block-wrapper_paragraph">
        {{ item.lable }}
      </p>
      <div class="bar">
        <div
          :style="sigPosition(parseFloat(item.percent))"
          class="bar-inner"
        ></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(item.percent) * 100) }}
        </p>
      </div>
    </div>

    <div class="legend-1">
      База (поставили оценку ниже 4):
      {{ val414 }}
    </div>
    <div class="legend-2">
      &#42; Средняя оценка удовлетворенности по параметру
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  data() {
    return {
      rowKeysPercent: [
        "Row230",
        "Row231",
        "Row232",
        "Row233",
        "Row234",
        "Row235",
        "Row236",
        "Row237",
      ],
    };
  },
  props: ["val223", "val414", "slideBody", "matrixData"],
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
      return objForSorting.slice(0, 3);
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
          width: "calc(" + parseFloat(value) * 100 + "%)",
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
  width: 48.5%;
  height: 262px;
  margin: 30px 30px 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.header {
  height: 44px;
  display: flex;
  font-weight: bold;
  color: #000000;
  width: 400px;
  text-align: left;
  margin: 0 0 20px 21px;
}

.header-paragraph {
  margin: 15px 9px 0 0;
  width: 320px;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.header-bar {
  margin: 20px 0 0 0;
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
  background: #937545;
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
 