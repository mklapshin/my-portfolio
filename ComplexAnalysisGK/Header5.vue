<template>
  <div class="content">
    <h1 class="header1">Необходимость изменений, %</h1>
    <div class="comments">
      <div class="comment-line">
        {{ slideBody["matrix"]["Row210"]["Col1"] }}
      </div>
      <br />
      <div class="comment-line">
        {{ slideBody["matrix"]["Row211"]["Col1"] }}
      </div>
      <br />
      <div class="comment-line">
        {{ slideBody["matrix"]["Row212"]["Col1"] }}
      </div>
      <br />
    </div>
  </div>
</template>

<script>
export default {
  props: ["slideBody"],
};
</script>

<style scoped>
/*@import "@/assets/scss/main.scss";*/
.content {
  font-family: Inter;
  width: 100%;
  margin: 45px 0 0 10px;
  text-align: left;
}

.header1 {
  font-size: 18px;
  line-height: 21px;
  letter-spacing: 0.02em;
  font-weight: 500;
  margin: 10px 0 0 0;
}

.comments {
  width: 100%;
  /*height: 40px;*/
  margin: 17px 0 0 0;
  font-size: 14px;
  line-height: 12px;
}
</style>
 