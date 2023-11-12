<template>
  <Header />
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm-3">
        <Sidebar />
      </div>
      <main class="col-sm-9">
        <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
        <Doughnut :data="data.chartConfig" :options="options" />

      </main>
    </div>
  </div>
</template>

<script>

import Header from "./components/partial/header.vue";
import Sidebar from "./components/partial/sidebar.vue";

import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
  ArcElement
} from "chart.js";
import { Bar, Doughnut } from "vue-chartjs";
import * as chartConfig from './components/Charts/Data/chartConfig.js'

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
  ArcElement,
);

export default {
  name: "BarChart",
  components: { Bar, Doughnut, Header, Sidebar },
  data() {
    return {

      chartData: {
        labels: ["January", "February", "March"],
        datasets: [{ data: [40, 20, 12] }],
      },
      chartOptions: {
        responsive: true,
      },

      chartConfig,
    };
  },
};
</script>