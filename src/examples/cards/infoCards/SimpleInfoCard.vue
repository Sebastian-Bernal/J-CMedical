<script setup>
defineProps({
  direction: {
    type: String,
    default: "text-start",
  },
  variant: {
    type: String,
    default: "gradient",
  },
  size: {
    type: String,
    default: "md",
  },
  color: {
    type: String,
    default: "success",
  },
  icon: {
    type: [String, Object],
    required: true,
    component: String,
    color: String,
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
});

function backgroundColor(variant, color) {
  let colorValue;

  if (variant === "gradient") {
    colorValue = "bg-gradient-" + color;
  } else if (variant === "contained") {
    colorValue = "bg-" + color;
  }

  return colorValue;
}
</script>
<template>
  <div :class="direction">
    <div class="header-card-custom">
      <div class="icon icon-shape text-center border-radius-xl mt-md-n4 bg-custom-default"
        :class="`icon-${size}  shadow-${color}`">
        <i class="material-icons opacity-10" :class="typeof icon == 'object' ? icon.color : ''">{{ typeof icon ==
          "string" ? icon : icon.component }}</i>
      </div>
      <h5 class="mt-3">{{ title }}</h5>
    </div>
    <p>
      {{ description }}
    </p>
  </div>
</template>

<style scoped>
@media screen and (max-width: 768px) {
  .header-card-custom {
    display: flex;
    align-items: center;
    gap: 20px !important;
    margin: 0;
    padding: 0;
    margin-bottom: 10px;
  }

  .header-card h5{
    margin: 0px !important;
    padding: 0;
  }
}
</style>
