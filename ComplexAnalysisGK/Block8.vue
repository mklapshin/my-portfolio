<template>
  <div class="content">
    <div class="header">
      Лояльность к управляющей компании | индекс NPS компании Комфорт Сервис
    </div>
    <div class="block-wrapper">
      <div class="block1">
        <div class="graphs-wrapper__total">
          <div class="graphs-wrapper__total-block">
            <div class="graphs-wrapper__total-item item-green"></div>
            <div class="graphs-wrapper__total-text">Промоутеры</div>
          </div>
          <div class="graphs-wrapper__total-block">
            <div class="graphs-wrapper__total-item item-yellow"></div>
            <div class="graphs-wrapper__total-text">Нейтралы</div>
          </div>
          <div class="graphs-wrapper__total-block">
            <div class="graphs-wrapper__total-item item-red"></div>
            <div class="graphs-wrapper__total-text">Критики</div>
          </div>
        </div>
        <div class="bar-wrapper__2">
          <div class="bar-wrapper">
            <div :style="sigPosition(val170)" class="bar-inner bar-left">
              {{ roundToFixed0(parseFloat(val170) * 100) }}
            </div>
            <div :style="sigPosition(val171)" class="bar-inner bar-center">
              {{ roundToFixed0(parseFloat(val171) * 100) }}
            </div>
            <div :style="sigPosition(val172)" class="bar-inner bar-right">
              {{ roundToFixed0(parseFloat(val172) * 100) }}
            </div>
          </div>
        </div>
        <div class="block-for-legend">
          <div class="block1-legend-1">Индекс NPS</div>
          <div class="block1-legend-2">
            <p v-if="parseFloat(val173['val']) > 0">
              +
              {{ roundToFixed0(parseFloat(val173["val"])) }}
            </p>
            <p v-if="parseFloat(val173['val']) < 0">
              {{ roundToFixed0(parseFloat(val173["val"])) }}
            </p>
            <p class="nps-null" v-if="parseFloat(val173['val']) == 0">
              {{ roundToFixed0(parseFloat(val173["val"])) }}
            </p>
          </div>
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
        "Row180",
        "Row181",
        "Row182",
        "Row183",
        "Row184",
        "Row185",
        "Row186",
        "Row187",
        "Row188",
        "Row189",
        "Row190",
        "Row191",
        "Row192",
        "Row193",
        "Row194",
      ],
      rowsForBarriers: [
        "Row195",
        "Row196",
        "Row197",
        "Row198",
        "Row199",
        "Row200",
        "Row201",
        "Row202",
        "Row203",
        "Row204",
        "Row205",
        "Row206",
        "Row207",
        "Row208",
        "Row209",
      ],
    };
  },
  props: ["val170", "val171", "val172", "val173", "matrixData", "slideBody"],
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
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    sigPosition: function (value) {
      if (value != 0.0) {
        return {
          height: "calc(" + parseFloat(value) * 100 + "%)",
        };
      } else {
        return {
          height: "calc(" + 0 + "%)",
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
  height: 30px;
  margin: 10px 0 3px 26px;
  color: #000000;
  font-weight: 600;
  text-align: left;
}

.block-wrapper {
  width: 100%;
  height: 200px;
  margin: 0;
  display: flex;
}

.block1 {
  width: 400px;
  height: 180px;
  margin: 25px 5px 0 0;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}

.graphs {
  width: 40rem;
  height: 40rem;
  display: flex;
}

.pieLegend {
  width: 200px;
  height: 130px;
  margin: 20px 10px 0 19px;
}

.image {
  width: 180px;
  height: 120px;
}

.legendText {
  width: 200px;
  height: 40px;
  display: flex;
}

.label {
  font-size: 14px;
  line-height: 14px;
  width: 143px;
  height: 28px;
  text-align: left;
}

.block-for-legend {
  display: flex;
}

.block1-legend-1 {
  width: 140px;
  margin: 11px 40px 0 22px;
  text-align: left;
  font-size: 20px;
  line-height: 23px;
  letter-spacing: 0.02em;
}

.block1-legend-2 {
  width: 74px;
  margin: 1px 1px 0 11px;
  text-align: left;
  font-size: 30px;
  line-height: 35px;
  font-weight: bold;
  letter-spacing: 0.02em;
}

.nps-null {
  margin: 0 0 0 15px;
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
  width: 90%;
  margin: 0 0 0 16px;
}

.header-red {
  color: #da2a0b;
  margin: 0 0 15px 0;
  font-weight: 600;
}

.graphs-wrapper__total {
  width: 12.9rem;
  margin: 0.9rem 0.25rem 0 1.5rem;
}

.graphs-wrapper__total-2 {
  width: 10.87rem;
  margin: 0.5rem 0.25rem 0 0;
  font-weight: 600;
}

.graphs-wrapper__total-block {
  display: flex;
  margin: 0 0 1.3rem 0;
}

.graphs-wrapper__total-item {
  width: 1rem;
  height: 1rem;
  margin: 0 1rem 0 0;
}

.item-green {
  background-color: #1ea50d;
}

.item-yellow {
  background-color: #ebc936;
}

.item-red {
  background-color: #da2a0b;
}

.graphs-wrapper__item {
  width: 7.75rem;
  margin: 0 0 1.6875rem 0;
  padding: 0 0 0 0;
}

.bar-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 2.1875rem;
  height: 118px;
}

.bar-wrapper-2 {
  width: 50px;
  height: 120px;
  margin: 20px 0 0 0;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.bar-inner {
  width: 1.875rem;
  text-align: center;
  padding: 0.3125rem 0 0 0;
  margin: 0 1.25rem 0 0;
  font-size: 0.9rem;
}

.bar-inner-2 {
  width: 1.875rem;
  text-align: center;
  padding: 0.4125rem 0 0 0;
  margin: 0 1.25rem 0 0.14rem;
  font-size: 0.9rem;
}

.bar-left {
  background: #1ea50d;
}

.bar-center {
  background: #ebc936;
}

.bar-right {
  background: #da2a0b;
}
</style>
 