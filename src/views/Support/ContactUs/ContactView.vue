<script setup>
import { onMounted, ref, watch } from "vue";

//example components
import DefaultNavbar from "../../../examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../../examples/footers/FooterDefault.vue";

//image
import image from "../../../../public/mano-en-guante-medico-apuntando-la-tecnologia-medica-de-pantalla-virtual.jpg"

//material components
import MaterialInput from "../../../components/MaterialInput.vue";
import MaterialTextArea from "../../../components/MaterialTextArea.vue";
import MaterialButton from "../../../components/MaterialButton.vue";

// material-input
import setMaterialInput from "@/assets/js/material-input";
onMounted(() => {
  setMaterialInput();
});

const formData = ref({
  nombre: '',
  correo: '',
  nit: '',
  mensaje: '',
})

watch((formData) => (newValue) => {
  console.log(newValue)
})

function enviarMensaje () {
  console.log('enviando...')
}
</script>
<template>
  <!-- <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <DefaultNavbar
          :sticky="true"
          :action="{
            route: 'https://www.creative-tim.com/product/vue-material-kit-pro',
            color: 'bg-gradient-primary',
            label: 'Buy Now',
          }"
        />
      </div>
    </div>
  </div> -->
  <section>
    <div class="page-header min-vh-80">
      <div class="container">
        <div class="row">
          <div
            class="col-6 d-lg-flex d-none h-100 my-auto pe-0 position-absolute top-0 start-0 text-center justify-content-center flex-column">
            <div class="position-relative h-100 m-3 px-7 border-radius-lg d-flex flex-column justify-content-center"
              :style="{
                backgroundImage: `url(${image})`,
                backgroundSize: 'cover',
              }" loading="lazy"></div>
          </div>
          <div class="mt-8 col-xl-5 col-lg-6 col-md-7 d-flex flex-column ms-auto me-auto ms-lg-auto me-lg-5">
            <div class="card d-flex blur justify-content-center shadow-lg my-sm-0 my-sm-6 mt-8 mb-5">
              <div class="card-header p-0 position-relative mt-n4 mx-3 z-index-2 bg-transparent">
                <div class="bg-custom-default shadow-dark border-radius-lg p-3">
                  <h3 class="text-white mb-0">Contactanos</h3>
                </div>
              </div>
              <div class="card-body">
                <p class="pb-3">
                  Déjanos tus datos y un asesor especializado se pondrá en contacto contigo para brindarte la
                  información que necesitas.
                </p>
                <form id="contact-form" method="post" autocomplete="off">
                  <div class="card-body p-0 my-3">
                    <div class="row">
                      <div class="col-md-6">
                        <MaterialInput class="input-group-static mb-4" type="text" label="Nombre completo"
                          placeholder="Ej. Juan Perez" v-model="formData.nombre"/>
                      </div>
                      <div class="col-md-6 ps-md-2">
                        <MaterialInput class="input-group-static mb-4" type="email" label="Correo"
                          placeholder="juan@gmail.com" v-model="formData.correo"/>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-12">
                        <MaterialInput class="input-group-static mb-4" type="text" label="NIT"
                          placeholder="Digita NIT" v-model="formData.nit"/>
                      </div>
                    </div>
                    <div class="form-group mb-0 mt-md-0 mt-4">
                      <MaterialTextArea id="message" class="input-group-static mb-4" :rows="4"
                        placeholder="Necesito..." v-model="formData.mensaje">Como podemos ayudarte?</MaterialTextArea>
                    </div>
                    <div class="row">
                      <div class="col-md-12 text-center">
                        <MaterialButton @click="enviarMensaje" variant="gradient" color="bg-custom-default" class="mt-3 mb-0">Enviar mensaje
                        </MaterialButton>
                      </div>
                    </div>
                  </div>
                </form>

              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
