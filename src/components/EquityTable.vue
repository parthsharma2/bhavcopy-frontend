<template>
  <div
    class="overflow-x-auto bg-white rounded-lg shadow overflow-y-auto relative"
    style="max-height: 50vh;"
  >
    <table
      class="border-collapse table-auto w-full whitespace-no-wrap bg-white table-striped relative"
    >
      <thead>
        <tr class="text-left">
          <template v-for="(heading, idx) in headings">
            <th
              class="bg-gray-100 sticky top-0 border-b border-gray-200 px-6 py-2 text-gray-600 font-bold tracking-wider uppercase text-xs"
              :key="idx"
            >
              {{ heading }}
            </th>
          </template>
        </tr>
      </thead>
      <tbody>
        <template v-for="record in records">
          <tr :key="record.code">
            <template v-for="(heading, idx) in headings">
              <td
                :key="idx"
                class="border-dashed border-t border-gray-200 userId"
              >
                <span class="text-gray-700 px-6 py-3 flex items-center">
                  {{ record[heading] }}
                </span>
              </td>
            </template>
          </tr>
        </template>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "EquityTable",
  props: {
    records: {
      type: Array,
      required: true,
    },
  },
  computed: {
    headings() {
      return ["code", "name", "open", "high", "low", "close"];
    },
  },
};
</script>
