<template>
  <div id="app" class="container">
    <div class="row mt-5" v-if="arrPositive.length > 0">
      <div class="col">
        <h2>Positive</h2>
        <line-chart
          :chartData="arrPositive"
          :options="chartOptions"
          label="Positive"
        >
        </line-chart>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import moment from "moment";
import LineChart from "./LineChart.vue";

export default {
  name: "GraphItem",
  components: {
    LineChart,
  },
  data() {
    return {
      arrPositive: [],
      arrHopitalized: [],
      arrInclu: [],
      arrOnVentilators: [],
      arrRecovered: [],
      arrDeaths: [],
      chartOptions: {
        responsive: true,
        maintainAspectRadio: false,
      },
    };
  },
  async created() {
    const { data } = await axios.get(
      "https://api.covidtracking.com/v1/us/daily.json"
    );
    data.forEach((element, index) => {
      if (index >= 100) {
        return;
      }

      const date = moment(element.date, "YYYYMMDD").format("MM/DD");

      const {
        positive,
        hospitalizedCurrently,
        inIcuCurrently,
        onVentilatorCurrently,
        recovered,
        death,
      } = element;

      this.arrPositive.push({ date, total: positive });
      this.arrHopitalized.push({ date, total: hospitalizedCurrently });
      this.arrInclu.push({ date, total: inIcuCurrently });
      this.arrOnVentilators.push({ date, total: onVentilatorCurrently });
      this.arrRecovered.push({ date, total: recovered });
      this.arrDeaths.push({ date, total: death });
    });
  },
};
</script>
<style></style>
