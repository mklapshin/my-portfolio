<template>
  <div class="wrapper">
    <!--    <pre>-->
    <!--      {{ slideBody }}-->
    <!--    </pre>-->

    <Header
      :valText="matrixData['Row3']['Col2']"
      :valHeader="matrixData['Row3']['Col2']"
      :slideBody="slideBody"
    />

    <!--      {{ matrixData }}-->

    <div class="line1">
      <Block1
        :val1="matrixData['Row7']['Col2']"
        :val2="matrixData['Row8']['Col2']"
        :slideBody="slideBody"
      />
      <Block2
        :val3="matrixData['Row9']['Col2']"
        :val4="matrixData['Row10']['Col2']"
        :val5="matrixData['Row11']['Col2']"
        :val6="matrixData['Row12']['Col2']"
        :val7="matrixData['Row13']['Col2']"
        :slideBody="slideBody"
      />
      <Block3
        :val8="matrixData['Row15']['Col2']"
        :val9="matrixData['Row16']['Col2']"
        :val10="matrixData['Row17']['Col2']"
        :val11="matrixData['Row18']['Col2']"
        :val12="matrixData['Row19']['Col2']"
        :val13="matrixData['Row20']['Col2']"
        :val14="matrixData['Row14']['Col2']"
        :slideBody="slideBody"
      />
    </div>

    <div class="line2">
      <Block4
        :val15="matrixData['Row21']['Col2']"
        :val16="matrixData['Row22']['Col2']"
        :val17="matrixData['Row23']['Col2']"
        :val18="matrixData['Row24']['Col2']"
        :val19="matrixData['Row25']['Col2']"
        :val20="matrixData['Row26']['Col2']"
        :val21="matrixData['Row27']['Col2']"
        :val22="matrixData['Row28']['Col2']"
        :slideBody="slideBody"
      />
      <Block5
        :val23="matrixData['Row29']['Col2']"
        :val24="matrixData['Row30']['Col2']"
        :val25="matrixData['Row31']['Col2']"
        :val26="matrixData['Row32']['Col2']"
        :val27="matrixData['Row33']['Col2']"
        :val28="matrixData['Row34']['Col2']"
        :val29="matrixData['Row35']['Col2']"
        :val30="matrixData['Row36']['Col2']"
        :val31="matrixData['Row37']['Col2']"
        :val32="matrixData['Row38']['Col2']"
        :val33="matrixData['Row39']['Col2']"
        :val34="matrixData['Row40']['Col2']"
        :val35="matrixData['Row41']['Col2']"
        :val36="matrixData['Row42']['Col2']"
        :val37="matrixData['Row43']['Col2']"
        :val38="matrixData['Row44']['Col2']"
        :slideBody="slideBody"
      />
    </div>

    <Header2 :matrixData="matrixData" :slideBody="slideBody" />

    <Block6
      :val42="matrixData['Row48']['Col2']"
      :val43="matrixData['Row49']['Col2']"
      :val44="matrixData['Row50']['Col2']"
      :val45="matrixData['Row51']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Header3 :matrixData="matrixData" :slideBody="slideBody" />
    <Block7
      :val149="matrixData['Row155']['Col2']"
      :val150="matrixData['Row156']['Col2']"
      :val151="matrixData['Row157']['Col2']"
      :val152="matrixData['Row158']['Col2']"
      :val153="matrixData['Row159']['Col2']"
      :val154="matrixData['Row160']['Col2']"
      :val155="matrixData['Row161']['Col2']"
      :val156="matrixData['Row162']['Col2']"
      :val157="matrixData['Row163']['Col2']"
      :val158="matrixData['Row164']['Col2']"
      :val159="matrixData['Row165']['Col2']"
      :val160="matrixData['Row166']['Col2']"
      :val161="matrixData['Row167']['Col2']"
      :val162="matrixData['Row168']['Col2']"
      :val163="matrixData['Row169']['Col2']"
      :val164="matrixData['Row170']['Col2']"
      :val165="matrixData['Row171']['Col2']"
      :val166="matrixData['Row172']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Header4 :matrixData="matrixData" :slideBody="slideBody" />
    <Block8
      :val170="matrixData['Row176']['Col2']"
      :val171="matrixData['Row177']['Col2']"
      :val172="matrixData['Row178']['Col2']"
      :val173="matrixData['Row179']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block8_2
      :val310="matrixData['Row316']['Col2']"
      :val311="matrixData['Row317']['Col2']"
      :val312="matrixData['Row318']['Col2']"
      :val313="matrixData['Row319']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Header5 :matrixData="matrixData" :slideBody="slideBody" />
    <Block9
      :val207="matrixData['Row213']['Col2']"
      :val149="matrixData['Row155']['Col2']"
      :val150="matrixData['Row156']['Col2']"
      :val151="matrixData['Row157']['Col2']"
      :val152="matrixData['Row158']['Col2']"
      :val153="matrixData['Row159']['Col2']"
      :val154="matrixData['Row160']['Col2']"
      :val155="matrixData['Row161']['Col2']"
      :val156="matrixData['Row162']['Col2']"
      :val157="matrixData['Row163']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />

    <Block10
      :val223="matrixData['Row229']['Col2']"
      :val414="matrixData['Row420']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block11
      :val232="matrixData['Row238']['Col2']"
      :val415="matrixData['Row421']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block12
      :val238="matrixData['Row244']['Col2']"
      :val416="matrixData['Row422']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block13
      :val244="matrixData['Row250']['Col2']"
      :val417="matrixData['Row423']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block14
      :val249="matrixData['Row255']['Col2']"
      :val418="matrixData['Row424']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block15
      :val254="matrixData['Row260']['Col2']"
      :val419="matrixData['Row425']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block16
      :val262="matrixData['Row268']['Col2']"
      :val420="matrixData['Row426']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block17
      :val266="matrixData['Row272']['Col2']"
      :val421="matrixData['Row427']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Block18
      :val273="matrixData['Row279']['Col2']"
      :val422="matrixData['Row428']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
    <Header6 />
    <Block19
      :val282="matrixData['Row288']['Col2']"
      :val295="matrixData['Row301']['Col2']"
      :val297="matrixData['Row303']['Col2']"
      :val298="matrixData['Row304']['Col2']"
      :val299="matrixData['Row305']['Col2']"
      :val300="matrixData['Row306']['Col2']"
      :val301="matrixData['Row307']['Col2']"
      :val303="matrixData['Row309']['Col2']"
      :val304="matrixData['Row310']['Col2']"
      :val305="matrixData['Row311']['Col2']"
      :val306="matrixData['Row312']['Col2']"
      :val307="matrixData['Row313']['Col2']"
      :val308="matrixData['Row314']['Col2']"
      :val309="matrixData['Row315']['Col2']"
      :matrixData="matrixData"
      :slideBody="slideBody"
    />
  </div>
</template>

<script>
import Header from "./ComplexAnalysisGK/Header.vue";
import Block1 from "./ComplexAnalysisGK/Block1.vue";
import Block2 from "./ComplexAnalysisGK/Block2.vue";
import Block3 from "./ComplexAnalysisGK/Block3.vue";
import Block4 from "./ComplexAnalysisGK/Block4.vue";
import Block5 from "./ComplexAnalysisGK/Block5.vue";
import Block6 from "./ComplexAnalysisGK/Block6.vue";
import Header2 from "./ComplexAnalysisGK/Header2.vue";
import Block7 from "./ComplexAnalysisGK/Block7.vue";
import Header3 from "./ComplexAnalysisGK/Header3.vue";
import Block8 from "./ComplexAnalysisGK/Block8.vue";
import Block8_2 from "./ComplexAnalysisGK/Block8_2.vue";
import Block9 from "./ComplexAnalysisGK/Block9.vue";
import Block10 from "./ComplexAnalysisGK/Block10.vue";
import Block11 from "./ComplexAnalysisGK/Block11.vue";
import Block12 from "./ComplexAnalysisGK/Block12.vue";
import Block13 from "./ComplexAnalysisGK/Block13.vue";
import Block14 from "./ComplexAnalysisGK/Block14.vue";
import Block15 from "./ComplexAnalysisGK/Block15.vue";
import Block16 from "./ComplexAnalysisGK/Block16.vue";
import Block17 from "./ComplexAnalysisGK/Block17.vue";
import Block18 from "./ComplexAnalysisGK/Block18.vue";
import Header4 from "./ComplexAnalysisGK/Header4.vue";
import Header5 from "./ComplexAnalysisGK/Header5.vue";
import Block19 from "./ComplexAnalysisGK/Block19.vue";
import Slide6 from "./ComplexAnalysisGK/Slide6.vue";

export default {
  props: ["counted", "slideBody"],
  computed: {
    matrixData: function () {
      return this.counted["matrixData"];
    },
  },
  components: {
    Header,
    Block1,
    Block2,
    Block3,
    Block4,
    Block5,
    Header2,
    Slide6,
    Block6,
    Header3,
    Block7,
    Block8,
    Block8_2,
    Block9,
    Header4,
    Block10,
    Block11,
    Block12,
    Block13,
    Block14,
    Block15,
    Block16,
    Block17,
    Block18,
    Header5,
    Block19,
  },
};
</script>

<style scoped>
.wrapper {
  background: #f4f4f4;
  /*background: sandybrown;*/
  margin: 0 auto;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
  font-family: Inter;
}

.line1,
.line2 {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}
</style>