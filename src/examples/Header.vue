<script setup>
import downArrow from "@/assets/img/down-arrow.svg";
defineProps({
  image: {
    type: String,
    default: "",
  },
  title: {
    type: [String, Object],
    default: "",
    text: String,
    variant: {
      validator(value) {
        return ["h1", "h2", "h3", "h4", "h5", "h6"].includes(value);
      },
    },
    class: {
      type: String,
      default: "",
    },
  },
  description: {
    type: [String, Object],
    default: "",
    text: String,
    class: String,
  },
  mask: {
    type: String,
    default: "mask bg-[var(--color-default)] opacity-5",
  },
  center: {
    type: Boolean,
    default: false,
  },
  minHeight: {
    type: String,
    default: " min-vh-75",
  },
  fullWidth: {
    type: Boolean,
    default: false,
  },
});
</script>
<template>
  <header class="header-2">
    <div class="section-actions">
      <div class="buttons-custom">
        <button class="btn btn-primary" style="background-color: #dd9d5c;">Contactanos</button>
        <button class="btn btn-dark">Sobre Nosotros</button>
      </div>
    </div>

    <div class="section-buttons">
      <div class="buttons-custom">
        <a href="https://twitter.com/creativetim" target="_blank">A</a>
        <a href="https://www.facebook.com/CreativeTim/" target="_blank">F</a>
        <a href="https://www.facebook.com/CreativeTim/" target="_blank">W</a>
      </div>
    </div>

    <img :src="image" class="page-header-custom"/>
  </header>

  <div class="abajo">
    <div>
      <a href="#Inicio">
        <img :src="downArrow" alt="Abajo" width="20">
      </a>
    </div>
  </div>
  
</template>

<style scoped>
.page-header-custom {
  width: 100%;
  max-height: 100vh;
  object-fit: cover;
  z-index: 9;
  opacity: 0.99;
}

.logo {
  width: 100px;
  filter: invert(1);
}

.section-actions {
  position: absolute;
  top: 15px;
  left: 50px;
  z-index: 5;
}

.section-actions {
  position: absolute;
  top: 15px;
  left: 50px;
  z-index: 5;
}

.section-buttons {
  position: absolute;
  top: 15px;
  right: 50px;
  z-index: 5;
}

.buttons-custom {
  display: flex;
  gap: 20px;
}

.section-buttons a {
  border-radius: 50%;
  background-color: black;
  width: 2rem;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
}

.abajo {
  position: absolute;
  color: #f10000;
  bottom: 35px;
  left: 0;
  right: 0;
}

.abajo div {
  width: 100%;
  display: flex;
  justify-content: center;
}

.abajo img {
  animation: moverAbajoArriba 1.5s ease-in-out infinite;
}

@keyframes moverAbajoArriba {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(8px);
  }
  100% {
    transform: translateY(0);
  }
}

@media screen and (max-width: 724px) {
  .section-buttons {
    top: 10px;
    right: 20px;
  }

  .buttons-custom {
    gap: 1px;
  }

  .section-buttons a {
    width: 20px;
    height: 20px;
  }
}
</style>
