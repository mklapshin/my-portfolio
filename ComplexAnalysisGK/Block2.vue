<template>
  <div class="content">
    <h3 class="header">Количество человек в семье</h3>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">один</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val3)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val3) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">два</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val4)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val4) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">три</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val5)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val5) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">четыре</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val6)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val6) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">пять</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val7)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val7) * 100) }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  props: ["val3", "val4", "val5", "val6", "val7", "slideBody"],
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
  margin: 0 30px 30px 0;
  display: flex;
  font-family: Inter;
  flex-direction: column;
  text-align: left;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
}

.header {
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  color: #000000;
  width: 160px;
  height: 44px;
  text-align: left;
  margin: 20px 0 2px 21px;
}

.block-wrapper {
  display: flex;
  height: 26px;
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
  margin: 5px 0 0 21px;
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
  width: 180px;
  height: 26px;
}

.bar-inner {
  width: 2.875rem;
  margin: 0 8px 0 0;
  font-size: 1rem;
  color: #fff;
  background: #937545;
}

.bar-wrapper_text {
  margin: 5px 0 0 0;
}
</style>
 