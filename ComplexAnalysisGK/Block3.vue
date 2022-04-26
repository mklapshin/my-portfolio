<template>
  <div class="content">
    <h3 class="header">Количество детей до 16 лет</h3>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">до 2 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val8)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val8) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">3-5 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val9)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val9) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">6-7 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val10)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val10) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">8-10 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val11)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val11) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">11-14 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val12)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val12) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">15-16 лет</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val13)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val13) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">нет детей</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val14)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val14) * 100) }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  props: [
    "val8",
    "val9",
    "val10",
    "val11",
    "val12",
    "val13",
    "val14",
    "slideBody",
  ],
  methods: {
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
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
  width: 100%;
  height: 228px;
  background: #ffffff;
  border-radius: 5px;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  font-family: Inter;
}

.header {
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  color: #000000;
  width: 150px;
  height: 44px;
  text-align: left;
  margin: 20px 0 2px 21px;
}

.block-wrapper {
  display: flex;
  height: 18px;
  margin: 0 0 4px 0;
}

.block-wrapper:hover {
  background-color: #f0eeee;
}

.block-wrapper:active {
  background-color: #dedede;
}

.block-wrapper_paragraph {
  width: 100px;
  text-align: left;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 14px;
  letter-spacing: 0.02em;
  margin: 0 0 0 21px;
}

.text-wrapper {
  margin: 0 0.1rem 0 0;
  width: 19rem;
}

.bar-wrapper {
  width: 4rem;
  height: 18px;
  margin: 0 0 4px 0;
  display: flex;
  flex-direction: column;
  padding: 0 0 0 0;
}

.bar {
  display: flex;
  flex-direction: row;
  width: 180px;
  height: 18px;
}

.bar-inner {
  width: 2.875rem;
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #937545;
}
</style>
 