<template>
  <div id="app">
    <div class="bg-gray-50 h-screen">
      <div class="container mx-auto py-6 px-4">
        <h1 class="text-3xl py-4 border-b mb-10 border-gray-200">
          Bhavcopy - Equity
        </h1>
        <equity-table :records="records"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import EquityTable from "./components/EquityTable.vue";

export default {
  name: "App",
  components: {
    "equity-table": EquityTable,
  },
  data() {
    return {
      records: [],
      query: "",
    };
  },
  methods: {
    fetchRecords() {
      const apiURL = process.env.VUE_APP_API_URL || "http://localhost:8000/api";

      axios
        .get(`${apiURL}/equity`, { params: { q: this.query } })
        .then((response) => {
          this.records = response.data;
        });
    },
  },
  mounted() {
    this.fetchRecords();
  },
};
</script>
