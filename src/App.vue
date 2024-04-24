<script setup>
import { ref } from "vue";

import Tree from "@/components/tree/index.vue";
import Table from "@/components/table.vue";

const dataTree = ref([
  {
    id: 1,
    text: "Folder 1",
    children: [
      {
        id: 1.1,
        text: "Sub Folder 1.1",
        children: [
          {
            id: 1.11,
            text: "Sub Folder 1.1.1",
            children: [],
          },
        ],
      },
      {
        id: 1.2,
        text: "Sub Folder 1.2",
        children: [
          {
            id: 1.21,
            text: "Sub Folder 1.2.1",
            children: [],
          },
        ],
      },
    ],
  },
  {
    id: 2,
    text: "Folder 2",
    children: [
      {
        id: 2.1,
        text: "Sub Folder 2.1",
        children: [],
      },
    ],
  },
]);

const dataTable = ref([
  {
    id: 1,
    name: "Name 1",
    age: 10,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
  {
    id: 2,
    name: "Name 2",
    age: 20,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
  {
    id: 3,
    name: "Name 3",
    age: 30,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
  {
    id: 4,
    name: "Name 4",
    age: 40,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
  {
    id: 5,
    name: "Name 5",
    age: 50,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
  {
    id: 6,
    name: "Name 6",
    age: 60,
    address: "test address",
    tags: ["tag1", "tag2"],
  },
]);

const fields = ref([
  {
    key: "id",
    label: "id",
    thClass: "text-left",
    tdClass: "text-left",
  },
  {
    key: "name",
    label: "name",
    thClass: "text-center",
    tdClass: "text-center",
  },
  {
    key: "age",
    label: "age",
    thClass: "text-center",
    tdClass: "text-center",
  },
  {
    key: "address",
    label: "address",
    thClass: "text-center",
    tdClass: "text-center",
  },
  {
    key: "tags",
    label: "tags",
    thClass: "text-center",
    tdClass: "text-center",
  },
  {
    key: "actions",
    label: "actions",
    thClass: "text-center",
    tdClass: "text-center",
  },
]);
</script>

<template>
  <div>
    <div class="card">
      <Tree :data="dataTree" />
    </div>

    <div class="card">
      <Table :items="dataTable" :fields="fields" :loading="false">
        <template #row(5)>
          <td :colspan="fields.length">custom</td>
        </template>

        <template #field(tags)="{ item }"> {{ item }} </template>
        <template #field(actions)> actions </template>
      </Table>
    </div>
  </div>
</template>
