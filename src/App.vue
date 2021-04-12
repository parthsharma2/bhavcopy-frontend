<template>
  <div id="app">
    <div class="bg-gray-50 h-screen">
      <div class="container mx-auto py-6 px-4">
        <h1 class="text-3xl py-4 border-b mb-10 border-gray-200">
          Bhavcopy - Equity
        </h1>

        <div class="mb-4 flex justify-between items-center">
          <div class="flex-1 pr-4">
            <div class="relative w-1/3">
              <div class="absolute top-0 left-0 inline-flex items-center p-2">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="w-6 h-6 text-gray-400"
                  viewBox="0 0 24 24"
                  stroke-width="2"
                  stroke="currentColor"
                  fill="none"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <rect x="0" y="0" width="24" height="24" stroke="none"></rect>
                  <circle cx="10" cy="10" r="7" />
                  <line x1="21" y1="21" x2="15" y2="15" />
                </svg>
              </div>
              <input
                v-model="query"
                type="search"
                class="w-full pl-10 pr-4 py-2 rounded-lg shadow focus:outline-none focus:shadow-outline text-gray-600 font-medium"
                placeholder="Search"
                @change="fetchRecords"
              />
            </div>
          </div>
        </div>

        <equity-table :records="records" :loading="loading" />
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
      loading: true,
    };
  },
  methods: {
    fetchRecords() {
      const apiURL = process.env.VUE_APP_API_URL || "http://localhost:8000/api";

      this.loading = true;

      axios
        .get(`${apiURL}/equity`, { params: { q: this.query } })
        .then((response) => {
          this.records = response.data;
          this.loading = false;
        })
        .catch((err) => {
          console.error("An unexpected error occured!", err);
        });
    },
  },
  mounted() {
    this.fetchRecords();
  },
};
</script>
