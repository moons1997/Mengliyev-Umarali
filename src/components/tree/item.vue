<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  model: Object,
});

const isOpen = ref(true);
const isChilde = computed(() => {
  return props.model.children && props.model.children.length;
});

function toggle() {
  isOpen.value = !isOpen.value;
}
</script>

<template>
  <li>
    <div :class="{ childe: isChilde }" @click="toggle">
      <span v-if="isChilde">
        {{ isOpen ? "🔽" : "▶️" }}
      </span>
      <span v-else> 🏁 </span>
      {{ model.text }}
    </div>
    <ul v-show="isOpen" v-if="isChilde">
      <item class="item" v-for="model in model.children" :model="model"> </item>
    </ul>
  </li>
</template>
<style>
.childe {
  cursor: pointer;
}
</style>
