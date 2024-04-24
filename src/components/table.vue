<script setup>
const props = defineProps({
  items: Array,
  fields: Array,
  loading: Boolean,
});
</script>
<template>
  <div>
    <table class="my-table">
      <thead>
        <tr>
          <th
            v-for="(field, idx) in fields"
            :key="idx + 'th'"
            :class="field.thClass"
          >
            {{ field.label }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="loading">
          <td :colspan="fields.length">...loading</td>
        </tr>

        <tr v-for="(item, index) in items" :key="index + 'tr'" v-else>
          <slot :name="`row(${index + 1})`" :item="item">
            <td
              v-for="(field, idx) in fields"
              :key="idx + 'td'"
              :class="field.tdClass"
            >
              <slot :name="`field(${field.key})`" :item="item[field.key]">
                {{ item[field.key] }}
              </slot>
            </td>
          </slot>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
.my-table {
  border-collapse: collapse;
  margin: 25px 0;
  font-size: 0.9em;
  font-family: sans-serif;
  width: 100%;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
}
.my-table thead tr {
  background-color: #00a6ed;
  color: #ffffff;
  text-align: left;
}

.my-table th,
.my-table td {
  padding: 12px 15px;
}
.my-table tbody tr {
  border-bottom: 1px solid #dddddd;
}

.my-table tbody tr:nth-of-type(even) {
  background-color: #f3f3f3;
}

.my-table tbody tr:last-of-type {
  border-bottom: 2px solid #00a6ed;
}

.my-table tbody tr.active-row {
  font-weight: bold;
  color: #00a6ed;
}
</style>
