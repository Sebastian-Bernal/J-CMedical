<script setup>
import { onMounted, onUnmounted, ref } from "vue";
import image from '@/assets/img/products/banner-medico-con-medico-usando-equipo.jpg'

//example components
import NavbarDefault from "../../../examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../../examples/footers/FooterDefault.vue";
import Header from "../../../examples/Header.vue";

//Vue Material Kit 2 Pro components
import MaterialButton from "../../../components/MaterialButton.vue";
import MaterialInput from "../../../components/MaterialInput.vue"

//sections
import Information from "./Sections/CoworkingInformation.vue";
import Testimonials from "./Sections/CoworkingTestimonials.vue";
import AboutUs from "./Sections/CoworkingAboutUs.vue";
import Places from "./Sections/CoworkingPlaces.vue";
import { useAppStore } from "../../../stores";
import ContactView from "../../Support/ContactUs/ContactView.vue";

//hooks
const body = document.getElementsByTagName("body")[0];
onMounted(() => {
  body.classList.add("coworking");
  body.classList.add("bg-gray-200");
});
onUnmounted(() => {
  body.classList.remove("coworking");
  body.classList.remove("bg-gray-200");
});

const store = useAppStore()
function cerrarModal() {
  store.showModal = false
}
</script>
<template>
  <div class="container-custom"></div>

  <Header image="public/JYC_BANNER.png" title="." minHeight="min-vh-100"
  :description="{
    class: 'pe-md-5 me-md-5 opacity-8',
  }" mask="mask bg-gradient-dark opacity-0">
  </Header>

  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault darkText :sticky="true" />
      </div>
    </div>
  </div>

  <div id="Inicio" class="card card-body blur shadow-blur mx-3 mx-md-4 mt-n4 mb-4 pt-6" >
    <Information />
    <Testimonials />
    <AboutUs id="SobreNosotros" />
    <Places id="Productos" />
    <div id="Contactanos" class="container">
      <div class="my-10 py-5 bg-gradient-dark position-relative border-radius-xl" 
      style="background-image: url('public/JYC_BANNER.png'); background-size: cover; background-position: start;"
      loading="lazy">
      <div class="position-absolute top-0 start-0 w-100 h-100 bg-dark opacity-7"></div>

        <div class="container position-relative z-index-2">
          <div class="row container-contacto">
            <div class="col-lg-5 col-md-8 m-auto text-start">
              <h5 class="text-white mb-lg-0 mb-5">
                ¿Buscas un accesorio específico?<br />
                <span class="text-sm">Contáctanos y te ayudamos a encontrar la solución ideal para tu equipo.</span>
              </h5>
            </div>
            <div class="col-lg-6 m-auto">
              <div class="row">
                <div class="col-sm-4 col-6 ps-sm-0 ms-auto">
                  <button class="btn btn-primary" style="background-color: #dd9d5c;">
                    Contactanos
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <ContactView/>
  </div>

  <DefaultFooter />

  <!-- Modal productos -->
  <div class="fondo" v-if="store.showModal">
    <div class="modal-custom">
      <div class="header-modal-custom">
        <h3>{{ store.informacion.title }}</h3>
        <button @click="cerrarModal()" type="button" class="btn-close text-xl py-3 opacity-10" data-bs-dismiss="alert"
          aria-label="Close">
          <i class="material-icons text-xl font-weight-bold text-dark">close</i>
        </button>
      </div>
      <div class="header-modal-body">
        <!-- <img :src="store.informacion.image" alt="" loading="lazy"> -->
        <img v-for="image in store.informacion.images" :src="image" alt="" loading="lazy">
      </div>
    </div>
  </div>

</template>

<style scoped>
.contacto {
  background-color: #dd9d5c;
  color: white;
}

.contacto:hover {
  opacity: 0.75;
  color: white;
}

.btn-custom {
  border: none;
  border-radius: 10px;
  color: white;
  background-color: #0000ff;
  text-transform: uppercase;
  font-size: small;
  font-weight: bold;
}

.container-custom {
  background: linear-gradient(180deg,rgba(244, 244, 244, 1) 3%, rgba(34, 98, 163, 1) 40%, rgba(235, 237, 240, 1) 100%);
  height: 130vh;
  width: 100%;
  position: absolute;
  top: 0;
  z-index: 0;
}

.fondo {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 105099999999;
  display: flex;
  justify-content: center;
  align-items: center;
  backdrop-filter: blur(2px);
  overflow-y: none;
}

.modal-custom {
  background-color: #fff;
  border-radius: 12px;
  padding: 24px;
  width: 90%;
  max-width: 500px;
  max-height: 80vh;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
  overflow: hidden;
  position: relative;
}

.header-modal-custom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.header-modal-custom h3 {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 600;
}

.close-button {
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #333;
  transition: color 0.2s ease;
}

.close-button:hover {
  color: #ff4d4d;
}

.header-modal-body {
  display: flex;
  flex-direction: column;
  gap: 10px;
  justify-content: center;
  align-items: center;
  max-height: 60vh;
  min-height: 40vh;
  overflow-y: auto;
}

.header-modal-body img {
  max-width: 100%;
  max-height: 60vh;
  object-fit: contain;
  border-radius: 8px;
}

.container-contacto {
  display: flex;

}
</style>
