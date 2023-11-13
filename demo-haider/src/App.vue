<template>
  <Header />
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm-3">
        <Sidebar />
      </div>
      <main class="col-sm-9">
        <div class="row align-items-center">
          <div class="col-sm-6">
            <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
          </div>
          <div class="col-sm-6">
            <Doughnut :data="Doughnut" :options="chartOptions" />
          </div>
        </div>

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

      Doughnut: {
        labels: ["Daily", "Weekly", "Monthly", "Annually"],
        datasets: [
          {
            backgroundColor: ["#41B883", "#E46651", "#00D8FF", "#DD1B16"],
            data: [40, 200, 400, 48000],
          },
        ],
      }
    };
  },
};
</script>