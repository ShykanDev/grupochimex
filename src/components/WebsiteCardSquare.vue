<template>
  <div
    class="max-w-xl p-1 mx-auto  bg-white text-slate-700 shadow-lg rounded-xl hover:shadow-2xl hover:scale-[1.02] hover:border-2 hover:border-orange-600 transition-all ease-in-out duration-300 hover:bg-orange-50 hover:text-slate-800 ">
    <!-- Imagen superior -->
    <img :src="website.domainImgUrl" alt="Domain Preview" class="w-full rounded-2xl"
      onerror="this.src='https://via.placeholder.com/800x400/EAEAEA/808080?text=No+Image'">

    <!-- Contenido -->
    <div class="p-6">
      <!-- Encabezado -->
      <div class="flex items-start justify-between mb-4">
        <h2 class="text-2xl font-bold ">{{ currentDomain }}</h2>
        <span class="bg-green-100 text-green-800 text-sm font-medium px-2.5 py-0.5 rounded-full">Activo</span>
      </div>

      <!-- Información -->
      <div class="space-y-3">
        <div class="flex items-center">
          <!-- <svg class="w-5 h-5 mr-2 text-gray-500" fill="currentColor" viewBox="0 0 20 20">
            <path
              d="M9 6a3 3 0 11-6 0 3 3 0 016 0zM17 6a3 3 0 11-6 0 3 3 0 016 0zM12.93 17c.046-.327.07-.66.07-1a6.97 6.97 0 00-1.5-4.33A5 5 0 0119 16v1h-6.07zM6 11a5 5 0 015 5v1H1v-1a5 5 0 015-5z">
            </path>
          </svg> -->
          <!-- <p class="text-gray-600">Categoría: <span class="ml-1 ">{{ website.category }}</span></p> -->
        </div>
      </div>

      <!-- Descripción -->
      <p class="mt-4 text-lg  font-poppins">
        {{ website.domainDescription }}
      </p>

      <!-- Botón -->
      <div class="mt-6">
        <a :href="website.websiteUrl" target="_blank"
          class="flex items-center justify-center px-4 py-2 text-white transition-colors duration-200 bg-orange-600 rounded-lg hover:bg-orange-700">
          <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1">
            </path>
          </svg>
          Visitar Sitio
        </a>
      </div>
    </div>
  </div>
</template>


<script lang="ts" setup>
import { computed } from 'vue';
interface IWebsite {
  domainName: string[];
  domainDescription: string;
  domainImgUrl: string;
  category: string;
  creationDate: string;
  status: string;
  websiteUrl: string;
}
const props = defineProps({
  website: {
    type: Object as () => IWebsite,
    required: true
  },
})

// Due to $website prop has two ways to get the url(s), array if website has multiples domains (website.domainName) and website.websiteUrl if only has 1 domain, this function replaces (deletes) the "https:/"  when its only one domain
const currentDomain = computed(() => (props.website.domainName.length > 1) ? props.website.domainName[0] : props.website.websiteUrl.replace(/https:\/\//gi, ''));



</script>

<style scoped></style>
