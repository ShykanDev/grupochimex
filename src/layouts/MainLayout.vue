<template>
  <div class="flex flex-col min-h-screen">
    <!-- Header -->
    <header class="sticky top-0 z-50 shadow-md bg-white">
      <div
        class="py-5 flex flex-col md:flex-row items-center justify-center sm:pr-16 space-y-4 md:space-y-0 md:space-x-9">
        <!-- Logo / Marca -->
        <RouterLink :to="{ name: 'home' }"
          class="flex items-center space-x-2 text-xl font-bold font-urbanist text-gray-800 transition-colors rounded-md hover:text-blue-600  ">
          <img src="@/assets/sslLogoV3.png" alt="Logo" class="w-10 h-12">
          <img src="@/assets/IndoExportsLogoFinal.svg" alt="Logo" class="w-12 h-12">
          <div translate="no" class="text-base">
            <span class="text-sky-900">www</span>
            <span class="text-sky-950">.</span>
            <span class="text-orange-600">grupo</span>
            <span class="text-sky-700">chimex</span>
            <span class="text-sky-700">.</span>
            <span class="text-sky-700">com</span>
          </div>
        </RouterLink>

        <!-- Flags (se ubicarán debajo del logo en móvil y en línea en md) -->
        <div class="flex items-center space-x-4">
          <img src="@/assets/mx.svg" alt="Mexico" class="w-6 h-6 animate-fade-down animate-delay-[0.2s]">
          <img src="@/assets/cl.svg" alt="Chile" class="w-6 h-6 animate-fade-down animate-delay-[0.4s]">
          <img src="@/assets/cn.svg" alt="China" class="w-6 h-6 animate-fade-down animate-delay-[0.6s]">
          <img src="@/assets/de.svg" alt="Germany" class="w-6 h-6 animate-fade-down animate-delay-[0.8s]">
          <img src="@/assets/ae.svg" alt="UAE" class="w-6 h-6 animate-fade-down animate-delay-[1s]">
          <img src="@/assets/in.svg" alt="India" class="w-6 h-6 animate-fade-down animate-delay-[1.2s]">
          <!-- Menú hamburguesa para móviles -->
          <details class="md:hidden">
            <summary class="cursor-pointer">
              <svg class="w-6 h-6 text-gray-700 hover:text-blue-500 transition-colors duration-200" fill="none"
                stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16">
                </path>
              </svg>
            </summary>
            <nav
              class="mt-2 flex flex-col space-y-3 bg-white shadow-md rounded-md p-4 absolute right-0 top-full w-64 z-10">
              <!-- Datos de Contacto en el menú móvil -->
              <div class="flex flex-col space-y-2 mb-4">
                <div class="flex items-center space-x-2">
                  <i class="fas fa-phone text-orange-600"></i>
                  <a href="tel:+525563950179"
                    class="text-gray-800 text-sm font-medium hover:text-blue-500 transition-colors duration-200">
                    +52 55 6395 0179
                  </a>
                </div>
                <div class="flex items-center space-x-2">
                  <i class="fas fa-envelope text-orange-600"></i>
                  <a href="mailto:informes@grupochimex.com"
                    class="text-gray-800 text-sm font-medium hover:text-blue-500 transition-colors duration-200">
                    informes@grupochimex.com
                  </a>
                </div>
              </div>
              <!-- Enlaces de Navegación en el menú móvil -->
              <RouterLink :to="{ name: 'home' }"
                class="font-medium text-gray-700 hover:text-blue-500 transition-colors duration-200 block">
                Inicio
              </RouterLink>
              <RouterLink :to="{ name: 'about' }"
                class="font-medium text-gray-700 hover:text-blue-500 transition-colors duration-200 block">
                Contacto
              </RouterLink>
              <RouterLink :to="{ name: 'aboutUs' }"
                class="font-medium text-gray-700 hover:text-blue-500 transition-colors duration-200 block">
                Nosotros
              </RouterLink>
            </nav>
          </details>
        </div>

        <!-- Información de contacto y navegación para pantallas md en adelante -->
        <div class="hidden md:flex items-center space-x-6">
          <!-- Datos de Contacto -->
          <div class="flex items-center space-x-4">
            <div class="flex items-center space-x-2">
              <i class="fas fa-phone text-sky-600"></i>
              <a href="tel:+525563950179"
                class="text-gray-800 text-sm font-medium hover:text-blue-500 transition-colors duration-200">
                +52 55 6395 0179
              </a>
            </div>
            <div class="flex items-center space-x-2">
              <i class="fas fa-envelope text-orange-600"></i>
              <a translate="no" href="mailto:informes@grupochimex.com"
                class="text-gray-800 text-sm font-medium hover:text-blue-500 transition-colors duration-200">
                informes@grupochimex.com
              </a>
            </div>
          </div>
          <!-- Enlaces de Navegación -->
          <nav class="flex space-x-2 md:pr-16">
            <RouterLink v-if="route.name !== 'home'" :to="{ name: 'home' }"
              class="font-medium text-orange-600 hover:text-blue-500 transition-colors duration-200">
              <i class="fas fa-home mr-1"></i>Inicio
            </RouterLink>
            <RouterLink v-if="route.name !== 'about'" :to="{ name: 'about' }"
              class="font-medium text-orange-600 hover:text-blue-500 transition-colors duration-200">
              <i class="fas fa-envelope mr-1"></i>Contacto
            </RouterLink>
            <RouterLink v-if="route.name !== 'aboutUs'" :to="{ name: 'aboutUs' }"
              class="font-medium text-orange-600 hover:text-blue-500 transition-colors duration-200">
              <i class="fas fa-handshake mr-1"></i>Nosotros
            </RouterLink>
          </nav>
        </div>


      </div>
      <section class="bg-orange-500 w-full flex min-h-1 animate-fade-right animate-duration-[2s]">
        <!-- Puedes agregar contenido adicional aquí -->
      </section>
    </header>


    <!-- Main Content -->
    <main class="flex-1">
      <slot name="main"></slot>
    </main>

    <!-- Footer -->
    <footer class="px-6 py-8 text-white bg-orange-500 md:px-12">
      <div class="grid gap-8 mb-8 md:grid-cols-2">


        <div>
          <h3 class="mb-4 text-xl font-bold">Contacto</h3>
          <ul class="space-y-2 text-white">
            <li class="flex items-center space-x-2">
              <i class="fas fa-phone"></i>
              <a href="tel:+525563950179" class="text-white">
                <span>+52 55 6395 0179</span>
              </a>
            </li>
            <li translate="no" class="flex items-center space-x-2">
              <i class="fas fa-envelope"></i>
              <a href="mailto:informes@grupochimex.com" class="text-white">
                <span>informes@grupochimex.com</span>
              </a>
            </li>
            <li translate="no" class="flex items-center space-x-2">
              <i class="fas fa-map-marker-alt"></i>
              <span translate="no">Gutenberg #128 Anzures, Miguel Hidalgo, 11590 Ciudad de México</span>
            </li>
          </ul>
        </div>

        <div>
          <h3 class="mb-4 text-xl font-bold">Mapa</h3>
          <div class="flex space-x-4">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d15050.158369675277!2d-99.17607!3d19.432289!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85d1f8b32758939b%3A0xf34fbd07bc47d6dd!2sGutenberg%20128%2C%20Anzures%2C%20Miguel%20Hidalgo%2C%2011590%20Ciudad%20de%20M%C3%A9xico%2C%20CDMX!5e0!3m2!1sen!2smx!4v1738996784058!5m2!1sen!2smx"
              class="w-full h-64 rounded-md" style="border:0;" allowfullscreen="false" loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"></iframe>
          </div>
        </div>
      </div>

      <div class="pt-6 text-center borderwhiteder-gray-700 text-gray-50">
        <p>&copy; 2025 Grupo Chimex. Todos los derechos reservados.</p>
        <p class="mt-1 text-xs">Diseño por <small class="text-sm italic">PACA</small> <i
            class="text-sky-800 fas fa-tornado"></i></p>
      </div>
    </footer>
  </div>
</template>

<script lang="ts" setup>
import { RouterLink, useRoute } from 'vue-router';

// router variable to the navigation header (dynamic buttons to navigate to home or contact)
const route = useRoute();

// No se requiere lógica adicional para este ejemplo
</script>

<style scoped>
/* Puedes añadir estilos personalizados aquí si es necesario */
</style>
