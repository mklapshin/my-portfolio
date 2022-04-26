<template>
  <div class="content">
    <h3 class="header1">
      {{ slideBody["matrix"]["Row2"]["Col1"] }}
    </h3>
    <h1 class="header2">База (проживают в ЖК): {{ valText }}</h1>
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
  margin: 5px 0 16px 0;
  font-weight: normal;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: 0.02em;
  font-weight: 500;
  color: #bababa;
}
</style>
 