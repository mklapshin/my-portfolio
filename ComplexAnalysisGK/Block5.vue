<template>
  <div class="content">
    <h3 class="header">Сфера деятельности</h3>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Маркетинг, реклама, PR</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val23)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val23) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Журналистика, СМИ</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val24)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val24) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Финансы, налоги</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val25)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val25) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Медицина, фармацевт.</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val26)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val26) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Юриспруденция</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val27)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val27) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">IT-технологии</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val28)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val28) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Образование, наука</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val29)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val29) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Отели, рестораны</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val30)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val30) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Культура, музыка</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val31)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val31) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Строит-во, архитектура</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val32)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val32) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Сфера обслуживания</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val33)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val33) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Бухгалтерия, аудит</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val34)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val34) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Домохозяйка</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val35)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val35) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Студент(ка)</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val36)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val36) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Пенсионер</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val37)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val37) * 100) }}
        </p>
      </div>
    </div>
    <div class="block-wrapper">
      <p class="block-wrapper_paragraph">Другое</p>
      <div class="bar">
        <div class="bar-inner" :style="sigPosition(val38)"></div>
        <p class="bar-wrapper_text">
          {{ roundToFixed0(parseFloat(val38) * 100) }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  props: [
    "val23",
    "val24",
    "val25",
    "val26",
    "val27",
    "val28",
    "val29",
    "val30",
    "val31",
    "val32",
    "val33",
    "val34",
    "val35",
    "val36",
    "val37",
    "val38",
    "slideBody",
  ],
  methods: {
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
    sigPosition: function (value) {
      if (value != 0.0) {
        return {
          width: "calc(" + parseFloat(value) * 100 * 5.3 + "%)",
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
  width: calc(50% - 15px);
  height: 465px;
  margin: 0 0 0 0;
  background: #ffffff;
  border-radius: 5px;
  font-family: Inter;
}

.header {
  width: 170px;
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
  width: 180px;
  text-align: left;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 14px;
  letter-spacing: 0.02em;
  margin: 0 40px 0 21px;
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
  width: 176px;
  height: 18px;
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
}
</style>
 