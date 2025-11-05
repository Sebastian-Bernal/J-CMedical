<script setup>
import { useAppStore } from '../stores';
import { watch } from 'vue';

defineProps({
  color: {
    type: String,
    default: "success",
  },
  dismissible: {
    type: Boolean,
    default: false,
  },
  fontWeight: {
    type: String,
    default: "",
  },
});

const store = useAppStore()

function getClasses(color, dismissible, fontWeight) {
  let colorValue, dismissibleValue, fontWeightValue;

  colorValue = color && `alert-${color}`;

  dismissibleValue = dismissible ? "alert-dismissible fade show" : "";

  fontWeightValue = fontWeight ? `font-weight-${fontWeight}` : "";

  return `${colorValue} ${dismissibleValue} ${fontWeightValue}`;
}

function cerrarAlert() {
  store.showAlert = false
}
</script>
<template>
  <div v-if="store.showAlert" class="alert alert-dismissible fade show text-white shadow-dark d-flex align-items-center justify-content-center px-5" role="alert" style="height: 60px;"
    :class="getClasses(color, dismissible, fontWeight)">
    &nbsp;
    <slot />
    <button v-if="dismissible" type="button" class="btn-close text-lg py-3 opacity-10" aria-label="Close"
      @click="cerrarAlert">
      <span aria-hidden="true" class="text-lg font-weight-bold">&times;</span>
    </button>
  </div>

</template>
