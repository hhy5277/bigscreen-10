<template>
  <div class="h94 xpanel xpanel-bg-ranking ">
		<div class="reward-card-wrapper-left-50">
			<div class="reward-card-wrapper-20">
				<h3 class="left-h3">{{map1.titleName}}</h3>
			</div>
			<div class="reward-card-wrapper-80">
				<chart-view
						type="pictorialBar"
						:options="options1">
				</chart-view>
			</div>
		</div>
		<div  class="reward-card-wrapper-right-50">
			<div class="reward-card-wrapper-20">
				<h3 class="right-h3">{{map2.titleName}}</h3>
			</div>
			<div class="reward-card-wrapper-80">
				<chart-view
						type="radar"
						:options="options2">
				</chart-view>
			</div>
		</div>
	</div>
</template>

<script>
import indexMixin from "@/views/bigscreen/mixins/indexMixin.js";
import digMixin from "./../mixins/digMixin.js";
import ChartView from "@/components/charts/ChartView";

export default {
  name: "DigTemplateC",
  mixins: [indexMixin, digMixin],
  components: { ChartView },
  props: {
    configMap: Object,
    configList: Array,
  },
  data() {
    return {
      map1: {},
      map2: {},
      options1: {},
      options2: {}
    }
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.getOptions1();
      this.getOptions2();
    },
    getOptions1() {
      this.map1["titleName"] = "标题1";
      let options = this.getCahrtSplitBarOpts({
        main_color:'#FF2267',
        yAxis_max: 1000,
        yAxis_data: ["1名称1", "2名称2", "3名称3", "4名称4", "5名称5"],
        series_data: [
          { name: "1名称1", value: 1000, index: 1 },
          { name: "1名称2", value: 900, index: 2 },
          { name: "1名称3", value: 800, index: 3 },
          { name: "1名称4", value: 700, index: 4 },
          { name: "1名称5", value: 600, index: 5 }
        ],
        grid: {
          top: "1%",
          height: "90%",
          left: "25%",
          right: "20%",
        },
      });
      this.$set(this, "options1", options);
    },
     getOptions2() {
      this.map2["titleName"] = "标题2";
      let options = this.getCahrtSplitBarOpts({
        yAxis_max: 1000,
        yAxis_data: ["1名称1", "2名称2", "3名称3", "4名称4", "5名称5"],
        series_data: [
          { name: "1名称1", value: 1000, index: 1 },
          { name: "1名称2", value: 900, index: 2 },
          { name: "1名称3", value: 800, index: 3 },
          { name: "1名称4", value: 700, index: 4 },
          { name: "1名称5", value: 600, index: 5 }
        ],
        grid: {
          top: "1%",
          height: "90%",
          left: "25%",
          right: "20%",
        },
      });
      this.$set(this, "options2", options);
    }
  },
};
</script>
