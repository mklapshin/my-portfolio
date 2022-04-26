<template>
  <div class="content">
    <h1 class="header3">Социально-демографический портрет жильцов, %</h1>
    <div class="comments">
      <div class="comment-line">{{ slideBody["matrix"]["Row4"]["Col1"] }}</div>
      <br />
      <div class="comment-line">{{ slideBody["matrix"]["Row5"]["Col1"] }}</div>
      <br />
      <div class="comment-line">{{ slideBody["matrix"]["Row6"]["Col1"] }}</div>
      <br />
    </div>
  </div>
</template>

<script>
import numbFormat from "../../helpers/numberFormat";

export default {
  props: ["valText", "valHeader", "slideBody"],
  methods: {
    roundToFixed0: function (string) {
      return numbFormat(string, 0, ".", "");
    },
  },
};
</script>

<style scoped>
/*@import "@/assets/scss/main.scss";*/
.content {
  font-family: Inter;
  width: 100%;
  /*height: 218px;*/
  margin: 0 0 19px 0;
  text-align: left;
}

.comment-line {
  margin-bottom: 3px;
}

.header1 {
  font-family: Inter;
  font-size: 24px;
  line-height: 28px;
  font-weight: 600;
  letter-spacing: 0.02em;
  font-weight: 500;
  margin: 50px 0 0 0;
}

.header2 {
  margin: 0 0 40px 0;
  font-weight: normal;
  font-size: 12px;
  line-height: 12px;
  letter-spacing: 0.02em;
  font-weight: 500;
  color: #bababa;
}

.header3 {
  font-size: 18px;
  line-height: 21px;
  letter-spacing: 0.02em;
  font-weight: 500;
}

.comments {
  width: 100%;
  /*height: 40px;*/
  margin: 17px 0 0 0;
  font-size: 14px;
  line-height: 12px;
}
</style>
 