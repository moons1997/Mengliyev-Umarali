<script setup>
import Item from "@/components/tree/item.vue";

const props = defineProps({
  data: Array,
});
</script>
<template>
  <ul class="tree">
    <Item
      class="item"
      :model="item"
      v-for="(item, idx) in data"
      :key="idx + 1 + 'a'"
    />
  </ul>
</template>

<style></style>
