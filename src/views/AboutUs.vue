<template>
  <MainLayout>
    <template #main>
      <section id="sobre-nosotros" class="bg-gray-50 py-16 font-poppins">
        <div class="container mx-auto px-4">
          <!-- Encabezado -->
          <div class="text-center mb-12">
            <h2 class="text-4xl font-bold text-orange-700 mb-4">
              <i class="fas fa-info-circle mr-2"></i> ¿Quiénes Somos?
            </h2>
            <p class="text-lg text-gray-700">
              Con más de 30 años de experiencia, en Grupo Chimex nos destacamos por ser un puente confiable entre
              empresas internacionales y proveedores mexicanos.
            </p>
          </div>

          <!-- Contenido descriptivo -->
          <div class="max-w-4xl mx-auto text-gray-700 text-lg leading-relaxed space-y-6">
            <p>
              Nuestra trayectoria en el mercado nos ha permitido consolidar un servicio integral enfocado en la
              importación de productos desde México. Ofrecemos procesos de supervisión, auditoría y certificación que
              aseguran que cada envío cumpla con los estándares de calidad y seguridad más exigentes. Nuestro compromiso
              principal es facilitar importaciones seguras,
              eficientes y transparentes para nuestros clientes.
            </p>
            <p>
              Además, en Grupo Chimex creemos firmemente en la responsabilidad social. Por ello, tenemos diversas
              páginas web, en las que usted podrá interactuar con los demás usuarios en diversos temas, tenemos sitios
              que son enfocados en distintos temas de ayuda social, orientados a ayudarle.
              Nuestro compromiso ético y social se refleja en cada proyecto,
              buscando siempre poner a las personas y el bienestar del entorno en el centro de nuestras operaciones.
            </p>
            <p>
              Como parte de nuestra diversificación, ofrecemos una selecta línea de productos de medicina ayurvédica,
              que integran lo mejor de las tradiciones ancestrales con los estándares modernos de calidad. Estos
              productos naturales complementan nuestro portafolio y refuerzan nuestro compromiso de brindar soluciones
              integrales que optimicen tanto los procesos comerciales como el bienestar de nuestros clientes.
            </p>
            <p>
              Aún hay más por saber de nosotros, le invitamos a que conozca todas nuestras <RouterLink
                class="font-medium text-orange-600 hover:text-blue-500 transition-colors duration-200 underline"
                :to="{ name: 'home' }">páginas</RouterLink>, en las que usted podrá conocernos mejor, estamos siempre a
              su servicio, somos <span class="font-hammersmithone text-orange-600 italic">Grupo Chimex.</span>
            </p>
          </div>
          <div class="text-center mt-12">
            <p class="text-gray-700"></p>
          </div>
        </div>
      </section>


    </template>
  </MainLayout>
</template>

<script lang="ts" setup>
import MainLayout from '@/layouts/MainLayout.vue';


</script>

<style scoped></style>
