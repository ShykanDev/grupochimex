<template>
  <section>
    <MainLayout>
      <template #main>
        <section class="bg-white py-16 px-4 sm:px-6 lg:px-8 font-poppins">
          <div class="max-w-2xl mx-auto">
            <div class="text-center mb-12">
              <h2 class="text-3xl font-extrabold text-gray-900 sm:text-4xl">
                Contáctenos
              </h2>
              <div class="mt-4 bg-orange-700 h-1 w-20 mx-auto rounded-full"></div>
            </div>

            <form class="grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-8">
              <!-- Nombre -->
              <div class="relative">
                <label for="nombre" class="block text-sm font-medium text-gray-700 mb-1">Nombre</label>
                <div class="relative">
                  <input type="text" id="nombre"
                    class="w-full px-4 py-3 pl-11 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-700 focus:border-orange-700"
                    placeholder="Su nombre">
                  <i class="fas fa-user absolute left-3 top-1/2 transform -translate-y-1/2 text-orange-700"></i>
                </div>
              </div>

              <!-- Email -->
              <div class="relative">
                <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                <div class="relative">
                  <input type="email" id="email"
                    class="w-full px-4 py-3 pl-11 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-700 focus:border-orange-700"
                    placeholder="correo@ejemplo.com">
                  <i class="fas fa-envelope absolute left-3 top-1/2 transform -translate-y-1/2 text-orange-700"></i>
                </div>
              </div>

              <!-- Mensaje -->
              <div class="relative sm:col-span-2">
                <label for="mensaje" class="block text-sm font-medium text-gray-700 mb-1">Mensaje</label>
                <div class="relative">
                  <textarea id="mensaje" rows="4"
                    class="w-full px-4 py-3 pl-11 border border-gray-300 rounded-lg resize-none focus:outline-none focus:ring-2 focus:ring-orange-700 focus:border-orange-700"
                    placeholder="Escriba su mensaje aquí..."></textarea>
                  <i class="fas fa-comment-dots absolute left-3 top-4 text-orange-700"></i>
                </div>
              </div>

              <!-- Botón de enviar -->
              <div class="sm:col-span-2">
                <button type="submit"
                  class="w-full bg-orange-700 text-white px-6 py-3 rounded-lg font-medium hover:bg-orange-800 transition-colors duration-300">
                  <i class="fas fa-paper-plane mr-2"></i> Enviar mensaje
                </button>
              </div>
            </form>

            <p class="mt-8 text-center text-gray-600 text-sm">
              ¿Prefiere otro método? <br>
              <!-- <a href="#" class="text-orange-700 hover:text-orange-800 underline">Contáctanos por WhatsApp</a> -->
              <a href="https://wa.me/525562516687"
                class="text-green-700 text-sm font-semibold hover:text-blue-500 transition-colors duration-200">
                Contáctenos por Whatsapp
              </a>
            </p>
          </div>
        </section>
      </template>
    </MainLayout>
  </section>
</template>

<script lang="ts" setup>
import MainLayout from '@/layouts/MainLayout.vue';


</script>

<style scoped></style>
