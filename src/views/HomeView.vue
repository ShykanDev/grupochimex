<template>
  <MainLayout>
    <template #main>
      <article id="intro" class="w-full bg-slate-100 pt-7 scroll-mt-20">
        <!-- intro -->
        <section class="font-poppins px-8 py-1 bg-gray-50">
          <div class="container mx-auto">
            <h2 class="text-3xl font-semibold text-orange-600 text-center mb-6 animate-fade-up">
              Somos Grupo Chimex, una empresa con más de 30 años de experiencia en el sector
            </h2>
            <div class="space-y-4 overflow-hidden">
              <p class="text-gray-700 poppins text-lg leading-relaxed animate-fade-left">
                Nos encargamos del control y la administración integral de las páginas y dominios presentados en este
                portal. Gracias a nuestra amplia trayectoria, garantizamos la integridad, seguridad y el correcto
                funcionamiento de cada sitio bajo nuestra gestión.
              </p>
              <p class="text-gray-700 poppins text-lg leading-relaxed animate-fade-left animate-delay-[.2s]">
                Todas las páginas y dominios presentados en esta plataforma están bajo la gestión y propiedad de Grupo
                Chimex, quien posee los derechos correspondientes y se encarga de su administración.
              </p>
              <p class="text-gray-700 text-lg leading-relaxed animate-fade-left animate-delay-[.4s]">
                Nuestro compromiso es brindar información verificada y confiable, respaldada por décadas de experiencia
                en
                el sector.
              </p>
            </div>
          </div>
        </section>

        <!-- Search Bar -->
        <section class="w-full flex justify-center sticky top-45 md:top-25 z-40 mt-4">
          <div class="relative w-1/2 md:w-3/4 lg:w-1/3 hover:w-3/4 transition-all duration-300 ease-in-out">
            <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
              <i class="fas fa-search text-gray-500"></i>
            </div>
            <input @input="filterDomains" v-model="search" type="text" :placeholder="`Ejemplo: ${placeHolderSearch}`"
              class="block w-full p-4 pl-10 font-poppins text-base bg-white border border-gray-300 rounded-lg focus:ring-orange-500 focus:border-orange-500dark:focus:ring-orange-500 dark:focus:border-orange-500 outline-none shadow-md transition-all duration-300 ease-in-out">
          </div>
        </section>

        <!-- Buttons to toggle the cards view -->
        <article class="w-full flex justify-center gap-3 mt-3">
          <button @click="isCards = true"
            class="flex items-center bg-sky-500 text-white cursor-pointer px-4 py-2 rounded-lg font-poppins transition-colors duration-300 ease-in-out hover:bg-sky-700 focus:outline-none focus:ring-2 focus:ring-sky-500 focus:ring-opacity-50"
            :class="{ 'bg-sky-800 border-[1px] border-sky-600': isCards }">
            <i class="fas fa-th-large mr-2"></i>
            Tarjetas
          </button>
          <button @click="isCards = false"
            class="flex items-center bg-sky-500 text-white cursor-pointer px-4 py-2 rounded-lg font-poppins transition-colors duration-300 ease-in-out hover:bg-sky-700 focus:outline-none focus:ring-sky-500 focus:ring-opacity-50"
            :class="{ 'bg-sky-800 border-[1px] border-sky-600': !isCards }">
            <i class="fas fa-list mr-2"></i>
            Lista
          </button>
        </article>


        <section class="flex flex-wrap justify-center gap-3 py-10 ">
          <WebsiteCard v-for="(website, index) in websites" :key="index" class="animate-fade-up" :website="website"
            :show-card-square="isCards" />
        </section>

        <!-- button (actually an anchor) to go to top with fas fa  icon -->
        <a href="#intro"
          class="fixed bottom-4 right-4 bg-orange-600 text-white p-2 rounded-full ring-yellow-800 ring-2">
          <i class="fas fa-arrow-up"></i>
          Ir arriba
        </a>
      </article>
      <div class="max-w-4xl mx-auto bg-white p-6 rounded-lg shadow-md font-poppins">
        <h2 class="text-2xl font-bold mb-4 text-center">Seguridad y Privacidad</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div class="bg-blue-100 p-4 rounded-lg shadow-inner text-center">
            <i class="fas fa-lock text-4xl text-blue-500 mb-2"></i>
            <h3 class="text-xl font-semibold">Seguridad SSL</h3>
            <p class="text-gray-700">Esta página utiliza SSL para proteger tus datos.</p>
          </div>
          <div class="bg-green-100 p-4 rounded-lg shadow-inner text-center">
            <i class="fas fa-shield-alt text-4xl text-green-500 mb-2"></i>
            <h3 class="text-xl font-semibold">Privacidad Garantizada</h3>
            <p class="text-gray-700">No recopilamos información bancaria o personal.</p>
          </div>
          <div class="bg-yellow-100 p-4 rounded-lg shadow-inner text-center">
            <i class="fas fa-credit-card text-4xl text-yellow-500 mb-2"></i>
            <h3 class="text-xl font-semibold">Sin Costo</h3>
            <p class="text-gray-700">Nuestra página es segura y sin costo para ti.</p>
          </div>
        </div>
      </div>
    </template>
  </MainLayout>
</template>

<script lang="ts" setup>
import MainLayout from '@/layouts/MainLayout.vue';
import WebsiteCard from '@/components/WebsiteCard.vue';
import { onMounted, ref } from 'vue';

interface IWebsite {
  domainName: string[];
  domainDescription: string;
  domainImgUrl: string;
  category: string;
  creationDate: string;
  status: string;
  colorDomains: string[];
  websiteUrl: string;
}

// TODO: Place the contact info on top


// Original list of websites
const websitesOriginal = ref<IWebsite[]>([
  {
    domainName: [
      "www.comercioamerica.com",
      "www.controlcalidad.net",
      "www.negocioamerica.com",
      "www.qualitycontrolexports.com",
      "www.empresasamerica.com",
      "www.exportacionesamerica.com",
      "www.exportsamerica.net"
    ],
    domainDescription: "Supervisamos, auditamos y certificamos productos mexicanos para su éxito internacional. Garantizamos calidad, seguridad y cumplimiento de estándares. Facilitamos importaciones con documentación transparente y más de 30 años de experiencia como su puente confiable con proveedores mexicanos.",
    domainImgUrl: "https://i.ibb.co/ns9QgF92/image-15.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.comercioamerica.com"
  },

  {
    domainName: [
      "www.miexpareja.net",
      "www.mipareja.net",
      "www.miexnovia.com.mx",
      "www.miexnovio.com",
      "www.miexesposa.com",
      "www.miexesposo.com"
    ],
    domainDescription: "Comparte tus experiencias sobre estafas, engaños y problemas con exparejas, para ayudar a otros a evitar caer en las mismas trampas. En este sitio, exploramos cómo algunas exparejas pueden manipular, llevando a deudas, fraudes y abuso emocional. Aprende a identificar señales de advertencia y proteger tu estabilidad financiera y emocional. Se ofrecen consejos para protegerte, como mantener cuentas separadas, monitorear reportes de crédito y establecer límites financieros claros desde el principio.",
    domainImgUrl: "https://i.ibb.co/yckgvxtB/miexnovia.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miexpareja.net"
  },
  {
    domainName: [
      "www.balbalatkaar.com",
      "www.balbalatkar.com",
      "www.abusadordemenores.com",
      "www.maltratomenores.com",
      "www.bullyingestudiantil.com",
      "www.childrapist.com"
    ],
    domainDescription: "La violencia que afecta a los niños, como autores o como víctimas, es motivo de preocupación al rededor del mundo. Siendo un problema social existente desde hace ya varios años, se han creado organizaciones que protegen los derechos y salud integral de los niños",
    domainImgUrl: "https://i.ibb.co/1ff8n8mN/blab.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.balbalatkaar.com"
  },
  {
    domainName: [
      "www.asesoradehogar.com",
      "www.asesorahogar.com",
      "www.empleadodomestico.com",
      "www.nanadomestica.com",
      "www.nanahogar.com"
    ],
    domainDescription: "Bienvenido a nuestra comunidad, un espacio diseñado para conectar a asesoras del hogar y a quienes las contratan. Aquí podrás compartir tu experiencia, ya sea positiva o negativa, y ayudar a otros a tomar decisiones más informadas al elegir a la persona adecuada para su hogar. Cada historia es valiosa y puede hacer una gran diferencia. No dudes en dejar tu testimonio, ofrecer recomendaciones o incluso leer las experiencias de otros.",
    domainImgUrl: "https://i.ibb.co/fGQS0tqR/ases.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.asesoradehogar.com"
  },
  {
    domainName: [
      "www.soplete.com.mx",
      "www.microtorch.com.mx"
    ],
    domainDescription: "Los sopletes MicroTorch están fabricados con metales de alta calidad, garantizando un rendimiento superior y mayor durabilidad. Su diseño está optimizado para ofrecer eficiencia y seguridad en entornos como laboratorios, cocinas, vidrierías y talleres, cumpliendo con los más altos estándares. Reconocidos por su excelente calidad, nuestros sopletes cuentan con la certificación ISO 9001, lo que asegura productos seguros y de confianza.",
    domainImgUrl: "https://i.ibb.co/F4jqj10h/soplete.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.soplete.com.mx"
  },
  {
    domainName: ["www.foredom.com.mx"],
    domainDescription: "Somos importadores mayoristas de productos Foredom, especializados en motores para uso profesional. Con más de 30 años de experiencia en el mercado, ofrecemos una amplia variedad de productos, tanto de Foredom USA como de Foredom Asia, adaptados a las necesidades de nuestros clientes. Desde herramientas de precisión hasta equipos industriales, garantizamos durabilidad y alto rendimiento.",
    domainImgUrl: "https://i.ibb.co/DHcvVKWX/foredom.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.foredom.com.mx"
  },
  {
    domainName: [
      "www.hileratungsteno.com",
      "www.hilerajoyeria.com"
    ],
    domainDescription: "La hilera de tungsteno es una herramienta esencial para el trefilado de metales ferrosos y no ferrosos, ideal para la creación de productos de joyería manual. Su alta resistencia al desgaste y tirones suaves hacen que el trefilado sea más eficiente y preciso. Esta herramienta permite reducir el grosor de alambres de diferentes metales, como oro, plata, cobre, platino y otros, aumentando la longitud mientras disminuye el diámetro. ",
    domainImgUrl: "https://i.ibb.co/5XjPgsCJ/hileratung.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.hileratungsteno.com"
  },
  {
    domainName: [
      "www.etiquetajoyeria.com",
      "www.etiquetastyvek.com"
    ],
    domainDescription: "Las etiquetas especiales para joyería y otros usos diversos están disponibles en diferentes tamaños, modelos y formas. Las etiquetas hechas de Tyvek de Dupont ofrecen una resistencia superior a tirones, vapor y humedad gracias a su composición de microfibras de tela. Estas etiquetas no tienen adhesivo en el centro, evitando manchas o daños en las joyas, y su material termoplástico las hace resistentes a líquidos. Además, se ofrecen productos como hileras de tungsteno y arcos alemanes de alta calidad para joyeros y profesionales en diversos campos.",
    domainImgUrl: "https://i.ibb.co/pBnTTLTp/etiquetas.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.etiquetajoyeria.com"
  },
  {
    domainName: [
      "www.arcosierra.com",
      "www.sawframe.com",
      "www.arcosegueta.com"
    ],
    domainDescription: "Los arcos y seguetas premium, como el modelo Arco Germany, están fabricados con acero de alta calidad y origen alemán, conocido por su resistencia a impactos y su durabilidad en trabajos exigentes. Su diseño tipo U optimiza la presión y el rendimiento al calar diversos materiales. El mango de madera sólida proporciona un agarre cómodo y resistente, pintado en negro piano. Además, el sistema ajustable del arco, con una perilla tipo mariposa, asegura que no haya movimiento indeseado al aplicar presión.",
    domainImgUrl: "https://i.ibb.co/SwLN6PSt/arcosierra.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.arcosierra.com"
  },
  {
    domainName: [
      "www.consultaespecializada.com",
      "www.consultaexperto.com",
      "www.consultagratisenlinea.com"
    ],
    domainDescription: "En nuestro sitio, puedes consultar a expertos de diversas áreas para resolver cualquier duda o recibir asesorías rápidas y eficaces. Ya sea que necesites hablar con un doctor, arquitecto, contador, o un especialista en marketing o servicios web, tendrás acceso directo a profesionales que te ayudarán a despejar tus inquietudes. Además, puedes contactarlos a través de diferentes medios como videollamadas, mensajes de texto o WhatsApp. El sitio ofrece un servicio cómodo y seguro, asegurando que encuentres la ayuda que necesitas en el menor tiempo posible.",
    domainImgUrl: "https://i.ibb.co/Cp3s9hxz/consulta-Exp.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.consultaespecializada.com"
  },
  {
    domainName: [
      "www.sopletesorca.com",
      "www.sopleteorca.com"
    ],
    domainDescription: "Los sopletes Orca, fabricados en Brasil, son herramientas de alta calidad y eficiencia para uso profesional en diversas áreas, desde trabajos rigurosos hasta detalles y manualidades. Con más de 50 años de experiencia, Orca es líder en la fabricación de sopletes, mecheros y otras herramientas especializadas para joyeros, artesanos del vidrio soplado, herreros, soldadores y más.",
    domainImgUrl: "https://i.ibb.co/jdDWWs3/sopletes-Orca.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.sopletesorca.com"
  },
  {
    domainName: ["www.oficiomaestro.com"],
    domainDescription: "En este sitio, puedes conocer experiencias de otros usuarios sobre diversos oficios y profesiones, como albañiles, dentistas, plomeros, abogados, carpinteros, pintores, mecánicos, y más. A través de los comentarios de quienes han contratado estos servicios, obtendrás recomendaciones, advertencias y sugerencias sobre los trabajos realizados. Esto te ayudará a tomar decisiones informadas y evitar problemas en el futuro.",
    domainImgUrl: "https://i.ibb.co/gNVBsMJ/oficio-Maestro.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.oficiomaestro.com"
  },
  {
    domainName: [
      "www.marcasbuenas.com",
      "www.marcasmalas.com"
    ],
    domainDescription: "En esta plataforma, puede acceder a una amplia variedad de comentarios y experiencias de miles de usuarios sobre diferentes marcas y productos. Desde maquillaje y ropa hasta tecnología como celulares, laptops y vehículos, los usuarios comparten sus vivencias para ayudarte a tomar decisiones más informadas. Las categorías incluyen recomendaciones, comparaciones y advertencias sobre marcas, lo que te permite conocer tanto lo positivo como lo negativo de cada producto o servicio.",
    domainImgUrl: "https://i.ibb.co/Txn2Sv24/marcas-Buenas.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.marcasbuenas.com"
  },
  {
    domainName: [
      "www.misdenuncias.com",
      "www.midenuncia.net",
      "www.misreclamos.com"
    ],
    domainDescription: "Misdenuncias.com es una plataforma donde puede compartir sus experiencias y reclamos sobre productos, servicios, empresas y más. Además, puede leer las experiencias de otros usuarios y obtener referencias o advertencias sobre distintos sectores como bancos, salud, comida, transporte, tecnología, entre otros. El registro es gratuito, y se incluyen diversas categorías de productos y servicios, permitiendo que cada usuario comente o consulte sobre diversas áreas.",
    domainImgUrl: "https://i.ibb.co/FLKSx48Q/misrecla.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.misdenuncias.com"
  },
  {
    domainName: [
      "www.hostigamiento.com",
      "www.acosadores.com"
    ],
    domainDescription: "Sitio donde se delatan las empresas, servicios y personas que cometen acciones de acoso y hostigamiento en cualquiera de sus modalidades. Comparta sus experiencias para informar a las demás personas sobre situaciones de hostigamiento o acoso de forma segura y gratuita",
    domainImgUrl: "https://i.ibb.co/mCGSm4X7/acosohostigamiento.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.hostigamiento.com"
  },
  {
    domainName: [
      "www.miarrendatario.com",
      "www.miarrendador.com"
    ],
    domainDescription: "Este sitio permite a arrendadores y arrendatarios compartir y consultar referencias sobre terceros para tomar decisiones informadas. Es gratuito, seguro y enfocado exclusivamente en experiencias de alquiler. Los usuarios pueden filtrar por tipo de inmueble, como casas, departamentos o locales, y deben iniciar sesión para comentar o visualizar opiniones. Los datos personales están protegidos y no se usan con otros fines.",
    domainImgUrl: "https://i.ibb.co/GvZvp3XP/miarrend.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miarrendatario.com"
  },
  {
    domainName: [
      "www.miempleador.com",
      "www.miempleado.net",
      "www.miexempleado.com",
      "www.miexempleador.com"
    ],
    domainDescription: "Descubra referencias sobre empleados y empleadores basadas en experiencias reales. Consulte antecedentes, recomendaciones, problemas legales, incumplimientos de contrato y fraudes laborales. Filtre por categorías o busca nombres específicos. Próximamente, asesorías legales gratuitas. Ideal para tomar decisiones informadas antes de contratar o aceptar un empleo.",
    domainImgUrl: "https://i.ibb.co/jP3hCxpQ/mireclamos.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miempleador.com"
  },
  {
    domainName: ["www.losestafadores.com"],
    domainDescription: "Una plataforma gratuita donde puedes consultar y compartir experiencias sobre fraudes y estafas cometidos por personas, empresas o servicios. Ofrece una búsqueda avanzada, comentarios verificados y un blog con información útil. Al registrarte, puedes comentar y responder a otros usuarios. Ideal para investigar antes de realizar compras, negocios o contrataciones y evitar riesgos financieros.",
    domainImgUrl: "https://i.ibb.co/1fhj6rzH/losestafa.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.losestafadores.com"
  },
  {
    domainName: [
      "www.mideudor.com",
      "www.misdeudores.com"
    ],
    domainDescription: "Este sitio permite compartir experiencias sobre los deudores en diversas formas, abordando consecuencias y lecciones aprendidas. Los usuarios pueden publicar comentarios sobre distintos tipos de deudas (monetarias, morales, sociales, etc.) y acceder a historias de otros para fomentar la reflexión y la transparencia. La plataforma es gratuita y segura, promoviendo el diálogo entre los participantes. Regístrate para contribuir y explorar experiencias compartidas por la comunidad.",
    domainImgUrl: "https://i.ibb.co/BKtJ0b4R/misdeudores.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mideudor.com"
  },
  {
    domainName: [
      "www.miciberseguridad.com",
      "www.cuentahackeada.com"
    ],
    domainDescription: "Este sitio le ayuda a proteger tus cuentas y evitar hackeos mediante estrategias de ciberseguridad. Aprenderá sobre tácticas de ciberdelincuentes como phishing, robo de identidad y vulnerabilidades de software. Además, ofrece consejos para fortalecer la seguridad de sus cuentas, mantener sus dispositivos protegidos y responder ante posibles ataques. La prevención es clave para reducir riesgos y evitar pérdidas financieras o de información.",
    domainImgUrl: "https://i.ibb.co/PZgDrPDy/cuentahack.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miciberseguridad.com"
  },
  {
    domainName: ["www.mantenimientocondominio.com"],
    domainDescription: "Esta plataforma facilita la gestión de condominios para administradores y propietarios. Los administradores pueden crear reportes, publicar avisos, gestionar encuestas y resolver problemas. Los propietarios pueden reportar incidencias, comentar temas de la comunidad y dar retroalimentación. El objetivo es mejorar la comunicación y la convivencia en los condominios.",
    domainImgUrl: "https://i.ibb.co/N6tHrtL2/mantenimientocond.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mantenimientocondominio.com"
  },
  {
    domainName: ["www.canastascestas.com"],
    domainDescription: "Nos especializamos en la venta de canastas de hierro forjado de alta calidad y resistencia, ideales para aportar elegancia y funcionalidad a cualquier espacio. Nuestras canastas, fabricadas con materiales duraderos y acabados refinados, están disponibles en una amplia variedad de modelos y tamaños, adecuados tanto para uso doméstico como comercial. Cada pieza combina diseño y solidez, ofreciendo una solución estética y práctica para diferentes necesidades de almacenamiento y decoración.",
    domainImgUrl: "https://i.ibb.co/7xsN3q6B/canastas-Cestas.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.canastascestas.com"
  },
  {
    domainName: [
      "www.harekrishna.com.mx",
      "www.radhakrishna.com.mx"
    ],
    domainDescription: "Descubra el movimiento Hare Krishna y el poder del Maha Mantra, un canto sagrado que eleva la conciencia espiritual. ISKCON, con templos en Vrindavan, Mumbai y Bengaluru, transmite su devoción en vivo. Conéctate con esta tradición de paz y amor divino.",
    domainImgUrl: "https://i.ibb.co/zWBKWC1L/harekrishna.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.harekrishna.com.mx"
  },
  {
    domainName: ["www.asafoetida.com.mx"],
    domainDescription: "Descubra los beneficios de la Asafoetida, un condimento natural y certificado 100% vegetariano, directamente desde la India. Potencie el sabor de sus platillos y aproveche sus propiedades medicinales. Visite nuestra página y adquiera un producto auténtico y de calidad.",
    domainImgUrl: "https://i.ibb.co/N4RvYJ8/asafoetida.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.asafoetida.com.mx"
  },
  {
    domainName: ["www.masplacerintimo.com"],
    domainDescription: "Redescubra el placer y la conexión en su vida íntima con InstaGo. Mejore su desempeño, aumente su confianza y fortalezca su relación con una fórmula natural y efectiva. Visite nuestra página y transforme su bienestar hoy mismo.",
    domainImgUrl: "https://i.ibb.co/QL8JHB6/masplacer.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.masplacerintimo.com"
  },
  {
    domainName: ["www.medicinaparaansiedad.com"],
    domainDescription: "Recupere la calma y el equilibrio con la medicina ayurvédica para la ansiedad. Olvídese del estrés y la tensión sin efectos secundarios ni dependencia. Descubra cómo los remedios naturales pueden ayudarle a alcanzar la paz mental de forma segura y efectiva. Visite nuestra página y comience su camino hacia el bienestar hoy mismo.",
    domainImgUrl: "https://i.ibb.co/XQF9cj0/medansiedad.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparaansiedad.com"
  },
  {
    domainName: ["www.medicinaparaartritis.com"],
    domainDescription: "Flex-Imac Forte le ayuda a aliviar el dolor articular y muscular de manera natural con la medicina ayurvédica, reduciendo la inflamación, mejorando su flexibilidad y fortaleciendo su cuerpo sin efectos secundarios, permitiéndole disfrutar de una vida sin limitaciones y mejorando su bienestar general.",
    domainImgUrl: "https://i.ibb.co/C3C22Ks1/med-Artritis.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparaartritis.com"
  },
  {
    domainName: ["www.medicinaparabajarpeso.com"],
    domainDescription: "La obesidad es una enfermedad crónica que se origina principalmente por el consumo excesivo de grasas, azúcares y carbohidratos, además de la falta de actividad física. Está relacionada con factores biológicos, sociales, culturales y psicológicos, y su tratamiento debe ser integral, involucrando médicos, nutriólogos, psicólogos y expertos en activación física. Para tratarla, es esencial mejorar la calidad y cantidad de los alimentos consumidos, realizar ejercicio físico, llevar un registro de lo que se come, y evitar el sedentarismo. Además, se recomienda consultar con un profesional de la salud para un control adecuado. En nuestra página, ofrecemos productos ayurvédicos 100% naturales, traídos directamente de la India, que pueden ayudarle en su camino hacia el control de la obesidad de manera efectiva y segura, apoyando su bienestar integral.",
    domainImgUrl: "https://i.ibb.co/Ps0C9bwJ/medbajarpeso.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparabajarpeso.com"
  },
  {
    domainName: ["www.medicinaparacolesterol.com"],
    domainDescription: "En esta página encontrará productos ayurvédicos 100% naturales diseñados para ayudar a controlar el colesterol alto de manera eficaz y segura. Nuestros productos están elaborados con ingredientes originarios de la India, siguiendo procesos milenarios que garantizan su calidad y efectividad. Además, todos nuestros productos cuentan con los certificados necesarios que aseguran su consumo seguro. Si tiene alguna duda o pregunta, no dude en contactarnos por correo y le responderemos a la brevedad. Prasadam es una marca mexicana que ofrece productos ayurvédicos para mejorar su salud y bienestar, incluyendo opciones para controlar el colesterol, bajar de peso y apoyar el manejo de la diabetes.",
    domainImgUrl: "https://i.ibb.co/TBXXCByq/Med-Colesterol.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparacolesterol.com"
  },
  {
    domainName: ["www.medicinaparacruda.com"],
    domainDescription: "HANGOVER es tu solución natural para aliviar los efectos de la resaca y el desvelo. Este suplemento 100% natural está compuesto por ingredientes ayurvédicos como la Ashwagandha y el Amla, conocidos por sus propiedades restauradoras que equilibran el cuerpo, reducen la inflamación y mejoran la digestión.",
    domainImgUrl: "https://i.ibb.co/Ps72G1LR/resaca.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparacruda.com"
  },
  {
    domainName: ["www.medicinaparadepresion.com"],
    domainDescription: "La depresión es una enfermedad caracterizada por una tristeza persistente y la pérdida de interés en las actividades cotidianas, afectando la capacidad para realizar tareas diarias durante al menos dos semanas. Los síntomas incluyen fatiga, cambios en el apetito, alteraciones en el sueño, ansiedad, y sentimientos de inutilidad, entre otros.",
    domainImgUrl: "https://i.ibb.co/7NpQ6NCt/Med-Depresion.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparadepresion.com"
  },
  {
    domainName: ["www.medicinaparadiabetes.com"],
    domainDescription: "Conozca Glufac, su aliado 100% natural para el control de la diabetes. Este suplemento está diseñado para ayudarle a regular los niveles de glucosa y mantener una vida equilibrada. Basado en la medicina ayurvédica, Glufac combina ingredientes poderosos que no solo apoyan el control de la diabetes, sino que también fortalecen el sistema inmunológico y mejoran la digestión. Si busca una solución natural para mantener su salud, Glufac es la opción ideal.",
    domainImgUrl: "https://i.ibb.co/rRd8GSfG/meddiabetes.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparadiabetes.com"
  },
  {
    domainName: ["www.medicinaparagastritis.com"],
    domainDescription: "CIDNI es un suplemento 100% natural inspirado en la medicina ayurvédica, diseñado para brindar alivio efectivo y duradero a quienes sufren de gastritis y otros trastornos estomacales. Su fórmula, que combina extractos de hierbas seleccionadas por sus propiedades digestivas y antiinflamatorias, actúa como un escudo natural contra el reflujo y la irritación estomacal. CIDNI ofrece una solución segura, libre de químicos dañinos, convirtiéndolo en una opción ideal para quienes buscan un enfoque natural para mejorar su salud digestiva.",
    domainImgUrl: "https://i.ibb.co/yccvLp3q/medgastritis.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparagastritis.com"
  },
  {
    domainName: ["www.medicinaparahemorroides.com"],
    domainDescription: "PILOGUARD es un suplemento 100% natural formulado para tratar las hemorroides, inspirado en la medicina ayurvédica. Su fórmula combina extractos de plantas conocidas por sus propiedades antiinflamatorias, astringentes y regenerativas, proporcionando alivio inmediato al dolor, la inflamación y la irritación en la región anal. Además, fortalece el sistema digestivo y vascular, combatiendo tanto los síntomas como las causas subyacentes de las hemorroides. PILOGUARD ofrece una solución natural, segura y libre de químicos agresivos, promoviendo una mejor calidad de vida para quienes buscan un tratamiento eficaz y suave.",
    domainImgUrl: "https://i.ibb.co/4nykzgtC/medHemo.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparahemorroides.com"
  },
  {
    domainName: ["www.medicinaparahigado.com"],
    domainDescription: "LIVAD es un suplemento 100% natural basado en la medicina ayurvédica, formulado con hierbas como Amalaki, Guduchi y Bhringraj, conocidas por sus beneficios para la salud hepática. Este suplemento promueve la desintoxicación, regeneración y protección del hígado sin ingredientes sintéticos ni productos químicos artificiales, lo que lo hace una opción segura y eficaz para quienes buscan apoyar la función hepática de manera natural.",
    domainImgUrl: "https://i.ibb.co/FbLgW3tg/medHig.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparahigado.com"
  },
  {
    domainName: ["www.chyawanprash.com.mx"],
    domainDescription: "Chyawanprash es una mermelada negra tradicional de la medicina ayurvédica, con más de 4000 años de historia en la India, elaborada con más de 50 ingredientes naturales activos. Este potente multivitamínico combina hierbas, frutas, y minerales, incluyendo láminas de oro y plata reales, para ofrecer un sabor agridulce único y una serie de beneficios rejuvenecedores para mejorar la calidad de vida. 100% natural, libre de conservadores y químicos, Chyawanprash sigue los procesos ayurvédicos de Rasayana, que promueven la longevidad y el bienestar general, siendo una formulación ideal para revitalizar y fortalecer el cuerpo de manera integral.",
    domainImgUrl: "https://i.ibb.co/7dr66xbv/chyan.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.chyawanprash.com.mx"
  },
  {
    domainName: ["www.mosquitero.com.mx"],
    domainDescription: "Si estás buscando una solución efectiva para protegerte de los mosquitos sin complicaciones, nuestro innovador mosquitero para cama es la respuesta que necesitas. Diseñado para adaptarse perfectamente a cualquier cama, este mosquitero integrado te garantiza noches de descanso reparador, sin esos molestos zumbidos. Ideal para el hogar o de viaje, su diseño plegable y portátil te ofrece comodidad y máxima protección.",
    domainImgUrl: "https://i.ibb.co/tTH68HNg/mosquitero.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mosquitero.com.mx"
  },
  {
    domainName: ["www.pastaneem.com"],
    domainDescription: "La pasta dental NEEM de PRASADAM está elaborada con extracto de Neem, un árbol originario de la India conocido por sus poderosas propiedades antibacterianas. 100% vegetariana y libre de fluor, esta pasta es ideal para mantener tu higiene bucal de manera natural. Ayuda a eliminar la placa dental, combate el mal aliento, previene las caries al crear una capa protectora sobre los dientes y combate la gengivitis, manteniendo las encías saludables. ",
    domainImgUrl: "https://i.ibb.co/DggwhdN3/pastaneem.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.pastaneem.com"
  },
]);

// Copy of the original list of websites that will be used for the filter function

const websites = ref<IWebsite[]>([
  {
    domainName: [
      "www.comercioamerica.com",
      "www.controlcalidad.net",
      "www.negocioamerica.com",
      "www.qualitycontrolexports.com",
      "www.empresasamerica.com",
      "www.exportacionesamerica.com",
      "www.exportsamerica.net"
    ],
    domainDescription: "Supervisamos, auditamos y certificamos productos mexicanos para su éxito internacional. Garantizamos calidad, seguridad y cumplimiento de estándares. Facilitamos importaciones con documentación transparente y más de 30 años de experiencia como su puente confiable con proveedores mexicanos.",
    domainImgUrl: "https://i.ibb.co/ns9QgF92/image-15.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.comercioamerica.com"
  },
  {
    domainName: ["www.foredom.com.mx"],
    domainDescription: "Somos importadores mayoristas de productos Foredom, especializados en motores para uso profesional. Con más de 30 años de experiencia en el mercado, ofrecemos una amplia variedad de productos, tanto de Foredom USA como de Foredom Asia, adaptados a las necesidades de nuestros clientes. Desde herramientas de precisión hasta equipos industriales, garantizamos durabilidad y alto rendimiento.",
    domainImgUrl: "https://i.ibb.co/DHcvVKWX/foredom.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.foredom.com.mx"
  },
  {
    domainName: [
      "www.soplete.com.mx",
      "www.microtorch.com.mx"
    ],
    domainDescription: "Los sopletes MicroTorch están fabricados con metales de alta calidad, garantizando un rendimiento superior y mayor durabilidad. Su diseño está optimizado para ofrecer eficiencia y seguridad en entornos como laboratorios, cocinas, vidrierías y talleres, cumpliendo con los más altos estándares. Reconocidos por su excelente calidad, nuestros sopletes cuentan con la certificación ISO 9001, lo que asegura productos seguros y de confianza.",
    domainImgUrl: "https://i.ibb.co/F4jqj10h/soplete.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.soplete.com.mx"
  },
  {
    domainName: [
      "www.hileratungsteno.com",
      "www.hilerajoyeria.com"
    ],
    domainDescription: "La hilera de tungsteno es una herramienta esencial para el trefilado de metales ferrosos y no ferrosos, ideal para la creación de productos de joyería manual. Su alta resistencia al desgaste y tirones suaves hacen que el trefilado sea más eficiente y preciso. Esta herramienta permite reducir el grosor de alambres de diferentes metales, como oro, plata, cobre, platino y otros, aumentando la longitud mientras disminuye el diámetro. ",
    domainImgUrl: "https://i.ibb.co/5XjPgsCJ/hileratung.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.hileratungsteno.com"
  },
  {
    domainName: [
      "www.etiquetajoyeria.com",
      "www.etiquetastyvek.com"
    ],
    domainDescription: "Las etiquetas especiales para joyería y otros usos diversos están disponibles en diferentes tamaños, modelos y formas. Las etiquetas hechas de Tyvek de Dupont ofrecen una resistencia superior a tirones, vapor y humedad gracias a su composición de microfibras de tela. Estas etiquetas no tienen adhesivo en el centro, evitando manchas o daños en las joyas, y su material termoplástico las hace resistentes a líquidos. Además, se ofrecen productos como hileras de tungsteno y arcos alemanes de alta calidad para joyeros y profesionales en diversos campos.",
    domainImgUrl: "https://i.ibb.co/pBnTTLTp/etiquetas.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.etiquetajoyeria.com"
  },
  {
    domainName: [
      "www.arcosierra.com",
      "www.sawframe.com",
      "www.arcosegueta.com"
    ],
    domainDescription: "Los arcos y seguetas premium, como el modelo Arco Germany, están fabricados con acero de alta calidad y origen alemán, conocido por su resistencia a impactos y su durabilidad en trabajos exigentes. Su diseño tipo U optimiza la presión y el rendimiento al calar diversos materiales. El mango de madera sólida proporciona un agarre cómodo y resistente, pintado en negro piano. Además, el sistema ajustable del arco, con una perilla tipo mariposa, asegura que no haya movimiento indeseado al aplicar presión.",
    domainImgUrl: "https://i.ibb.co/SwLN6PSt/arcosierra.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.arcosierra.com"
  },
  {
    domainName: [
      "www.miexpareja.net",
      "www.mipareja.net",
      "www.miexnovia.com.mx",
      "www.miexnovio.com",
      "www.miexesposa.com",
      "www.miexesposo.com"
    ],
    domainDescription: "Comparte tus experiencias sobre estafas, engaños y problemas con exparejas, para ayudar a otros a evitar caer en las mismas trampas. En este sitio, exploramos cómo algunas exparejas pueden manipular, llevando a deudas, fraudes y abuso emocional. Aprende a identificar señales de advertencia y proteger tu estabilidad financiera y emocional. Se ofrecen consejos para protegerte, como mantener cuentas separadas, monitorear reportes de crédito y establecer límites financieros claros desde el principio.",
    domainImgUrl: "https://i.ibb.co/yckgvxtB/miexnovia.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miexpareja.net"
  },
  {
    domainName: [
      "www.balbalatkaar.com",
      "www.balbalatkar.com",
      "www.abusadordemenores.com",
      "www.maltratomenores.com",
      "www.bullyingestudiantil.com",
      "www.childrapist.com"
    ],
    domainDescription: "La violencia que afecta a los niños, como autores o como víctimas, es motivo de preocupación al rededor del mundo. Siendo un problema social existente desde hace ya varios años, se han creado organizaciones que protegen los derechos y salud integral de los niños",
    domainImgUrl: "https://i.ibb.co/1ff8n8mN/blab.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.balbalatkaar.com"
  },
  {
    domainName: [
      "www.asesoradehogar.com",
      "www.asesorahogar.com",
      "www.empleadodomestico.com",
      "www.nanadomestica.com",
      "www.nanahogar.com"
    ],
    domainDescription: "Bienvenido a nuestra comunidad, un espacio diseñado para conectar a asesoras del hogar y a quienes las contratan. Aquí podrás compartir tu experiencia, ya sea positiva o negativa, y ayudar a otros a tomar decisiones más informadas al elegir a la persona adecuada para su hogar. Cada historia es valiosa y puede hacer una gran diferencia. No dudes en dejar tu testimonio, ofrecer recomendaciones o incluso leer las experiencias de otros.",
    domainImgUrl: "https://i.ibb.co/fGQS0tqR/ases.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.asesoradehogar.com"
  },
  {
    domainName: [
      "www.soplete.com.mx",
      "www.microtorch.com.mx"
    ],
    domainDescription: "Los sopletes MicroTorch están fabricados con metales de alta calidad, garantizando un rendimiento superior y mayor durabilidad. Su diseño está optimizado para ofrecer eficiencia y seguridad en entornos como laboratorios, cocinas, vidrierías y talleres, cumpliendo con los más altos estándares. Reconocidos por su excelente calidad, nuestros sopletes cuentan con la certificación ISO 9001, lo que asegura productos seguros y de confianza.",
    domainImgUrl: "https://i.ibb.co/F4jqj10h/soplete.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.soplete.com.mx"
  },


  {
    domainName: [
      "www.consultaespecializada.com",
      "www.consultaexperto.com",
      "www.consultagratisenlinea.com"
    ],
    domainDescription: "En nuestro sitio, puedes consultar a expertos de diversas áreas para resolver cualquier duda o recibir asesorías rápidas y eficaces. Ya sea que necesites hablar con un doctor, arquitecto, contador, o un especialista en marketing o servicios web, tendrás acceso directo a profesionales que te ayudarán a despejar tus inquietudes. Además, puedes contactarlos a través de diferentes medios como videollamadas, mensajes de texto o WhatsApp. El sitio ofrece un servicio cómodo y seguro, asegurando que encuentres la ayuda que necesitas en el menor tiempo posible.",
    domainImgUrl: "https://i.ibb.co/Cp3s9hxz/consulta-Exp.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.consultaespecializada.com"
  },
  {
    domainName: [
      "www.sopletesorca.com",
      "www.sopleteorca.com"
    ],
    domainDescription: "Los sopletes Orca, fabricados en Brasil, son herramientas de alta calidad y eficiencia para uso profesional en diversas áreas, desde trabajos rigurosos hasta detalles y manualidades. Con más de 50 años de experiencia, Orca es líder en la fabricación de sopletes, mecheros y otras herramientas especializadas para joyeros, artesanos del vidrio soplado, herreros, soldadores y más.",
    domainImgUrl: "https://i.ibb.co/jdDWWs3/sopletes-Orca.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.sopletesorca.com"
  },
  {
    domainName: ["www.canastascestas.com"],
    domainDescription: "Nos especializamos en la venta de canastas de hierro forjado de alta calidad y resistencia, ideales para aportar elegancia y funcionalidad a cualquier espacio. Nuestras canastas, fabricadas con materiales duraderos y acabados refinados, están disponibles en una amplia variedad de modelos y tamaños, adecuados tanto para uso doméstico como comercial. Cada pieza combina diseño y solidez, ofreciendo una solución estética y práctica para diferentes necesidades de almacenamiento y decoración.",
    domainImgUrl: "https://i.ibb.co/7xsN3q6B/canastas-Cestas.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.canastascestas.com"
  },
  {
    domainName: ["www.oficiomaestro.com"],
    domainDescription: "En este sitio, puedes conocer experiencias de otros usuarios sobre diversos oficios y profesiones, como albañiles, dentistas, plomeros, abogados, carpinteros, pintores, mecánicos, y más. A través de los comentarios de quienes han contratado estos servicios, obtendrás recomendaciones, advertencias y sugerencias sobre los trabajos realizados. Esto te ayudará a tomar decisiones informadas y evitar problemas en el futuro.",
    domainImgUrl: "https://i.ibb.co/gNVBsMJ/oficio-Maestro.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.oficiomaestro.com"
  },
  {
    domainName: [
      "www.marcasbuenas.com",
      "www.marcasmalas.com"
    ],
    domainDescription: "En esta plataforma, puede acceder a una amplia variedad de comentarios y experiencias de miles de usuarios sobre diferentes marcas y productos. Desde maquillaje y ropa hasta tecnología como celulares, laptops y vehículos, los usuarios comparten sus vivencias para ayudarte a tomar decisiones más informadas. Las categorías incluyen recomendaciones, comparaciones y advertencias sobre marcas, lo que te permite conocer tanto lo positivo como lo negativo de cada producto o servicio.",
    domainImgUrl: "https://i.ibb.co/Txn2Sv24/marcas-Buenas.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.marcasbuenas.com"
  },
  {
    domainName: [
      "www.misdenuncias.com",
      "www.midenuncia.net",
      "www.misreclamos.com"
    ],
    domainDescription: "Misdenuncias.com es una plataforma donde puede compartir sus experiencias y reclamos sobre productos, servicios, empresas y más. Además, puede leer las experiencias de otros usuarios y obtener referencias o advertencias sobre distintos sectores como bancos, salud, comida, transporte, tecnología, entre otros. El registro es gratuito, y se incluyen diversas categorías de productos y servicios, permitiendo que cada usuario comente o consulte sobre diversas áreas.",
    domainImgUrl: "https://i.ibb.co/FLKSx48Q/misrecla.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.misdenuncias.com"
  },
  {
    domainName: [
      "www.hostigamiento.com",
      "www.acosadores.com"
    ],
    domainDescription: "Sitio donde se delatan las empresas, servicios y personas que cometen acciones de acoso y hostigamiento en cualquiera de sus modalidades. Comparta sus experiencias para informar a las demás personas sobre situaciones de hostigamiento o acoso de forma segura y gratuita",
    domainImgUrl: "https://i.ibb.co/mCGSm4X7/acosohostigamiento.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.hostigamiento.com"
  },
  {
    domainName: [
      "www.miarrendatario.com",
      "www.miarrendador.com"
    ],
    domainDescription: "Este sitio permite a arrendadores y arrendatarios compartir y consultar referencias sobre terceros para tomar decisiones informadas. Es gratuito, seguro y enfocado exclusivamente en experiencias de alquiler. Los usuarios pueden filtrar por tipo de inmueble, como casas, departamentos o locales, y deben iniciar sesión para comentar o visualizar opiniones. Los datos personales están protegidos y no se usan con otros fines.",
    domainImgUrl: "https://i.ibb.co/GvZvp3XP/miarrend.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miarrendatario.com"
  },
  {
    domainName: [
      "www.miempleador.com",
      "www.miempleado.net",
      "www.miexempleado.com",
      "www.miexempleador.com"
    ],
    domainDescription: "Descubra referencias sobre empleados y empleadores basadas en experiencias reales. Consulte antecedentes, recomendaciones, problemas legales, incumplimientos de contrato y fraudes laborales. Filtre por categorías o busca nombres específicos. Próximamente, asesorías legales gratuitas. Ideal para tomar decisiones informadas antes de contratar o aceptar un empleo.",
    domainImgUrl: "https://i.ibb.co/jP3hCxpQ/mireclamos.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miempleador.com"
  },
  {
    domainName: ["www.losestafadores.com"],
    domainDescription: "Una plataforma gratuita donde puedes consultar y compartir experiencias sobre fraudes y estafas cometidos por personas, empresas o servicios. Ofrece una búsqueda avanzada, comentarios verificados y un blog con información útil. Al registrarte, puedes comentar y responder a otros usuarios. Ideal para investigar antes de realizar compras, negocios o contrataciones y evitar riesgos financieros.",
    domainImgUrl: "https://i.ibb.co/1fhj6rzH/losestafa.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.losestafadores.com"
  },
  {
    domainName: [
      "www.mideudor.com",
      "www.misdeudores.com"
    ],
    domainDescription: "Este sitio permite compartir experiencias sobre los deudores en diversas formas, abordando consecuencias y lecciones aprendidas. Los usuarios pueden publicar comentarios sobre distintos tipos de deudas (monetarias, morales, sociales, etc.) y acceder a historias de otros para fomentar la reflexión y la transparencia. La plataforma es gratuita y segura, promoviendo el diálogo entre los participantes. Regístrate para contribuir y explorar experiencias compartidas por la comunidad.",
    domainImgUrl: "https://i.ibb.co/BKtJ0b4R/misdeudores.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mideudor.com"
  },
  {
    domainName: [
      "www.miciberseguridad.com",
      "www.cuentahackeada.com"
    ],
    domainDescription: "Este sitio le ayuda a proteger tus cuentas y evitar hackeos mediante estrategias de ciberseguridad. Aprenderá sobre tácticas de ciberdelincuentes como phishing, robo de identidad y vulnerabilidades de software. Además, ofrece consejos para fortalecer la seguridad de sus cuentas, mantener sus dispositivos protegidos y responder ante posibles ataques. La prevención es clave para reducir riesgos y evitar pérdidas financieras o de información.",
    domainImgUrl: "https://i.ibb.co/PZgDrPDy/cuentahack.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.miciberseguridad.com"
  },
  {
    domainName: ["www.mantenimientocondominio.com"],
    domainDescription: "Esta plataforma facilita la gestión de condominios para administradores y propietarios. Los administradores pueden crear reportes, publicar avisos, gestionar encuestas y resolver problemas. Los propietarios pueden reportar incidencias, comentar temas de la comunidad y dar retroalimentación. El objetivo es mejorar la comunicación y la convivencia en los condominios.",
    domainImgUrl: "https://i.ibb.co/N6tHrtL2/mantenimientocond.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mantenimientocondominio.com"
  },

  {
    domainName: [
      "www.harekrishna.com.mx",
      "www.radhakrishna.com.mx"
    ],
    domainDescription: "Descubra el movimiento Hare Krishna y el poder del Maha Mantra, un canto sagrado que eleva la conciencia espiritual. ISKCON, con templos en Vrindavan, Mumbai y Bengaluru, transmite su devoción en vivo. Conéctate con esta tradición de paz y amor divino.",
    domainImgUrl: "https://i.ibb.co/zWBKWC1L/harekrishna.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.harekrishna.com.mx"
  },
  {
    domainName: ["www.asafoetida.com.mx"],
    domainDescription: "Descubra los beneficios de la Asafoetida, un condimento natural y certificado 100% vegetariano, directamente desde la India. Potencie el sabor de sus platillos y aproveche sus propiedades medicinales. Visite nuestra página y adquiera un producto auténtico y de calidad.",
    domainImgUrl: "https://i.ibb.co/N4RvYJ8/asafoetida.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.asafoetida.com.mx"
  },
  {
    domainName: ["www.masplacerintimo.com"],
    domainDescription: "Redescubra el placer y la conexión en su vida íntima con InstaGo. Mejore su desempeño, aumente su confianza y fortalezca su relación con una fórmula natural y efectiva. Visite nuestra página y transforme su bienestar hoy mismo.",
    domainImgUrl: "https://i.ibb.co/QL8JHB6/masplacer.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.masplacerintimo.com"
  },
  {
    domainName: ["www.medicinaparaansiedad.com"],
    domainDescription: "Recupere la calma y el equilibrio con la medicina ayurvédica para la ansiedad. Olvídese del estrés y la tensión sin efectos secundarios ni dependencia. Descubra cómo los remedios naturales pueden ayudarle a alcanzar la paz mental de forma segura y efectiva. Visite nuestra página y comience su camino hacia el bienestar hoy mismo.",
    domainImgUrl: "https://i.ibb.co/XQF9cj0/medansiedad.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparaansiedad.com"
  },
  {
    domainName: ["www.medicinaparaartritis.com"],
    domainDescription: "Flex-Imac Forte le ayuda a aliviar el dolor articular y muscular de manera natural con la medicina ayurvédica, reduciendo la inflamación, mejorando su flexibilidad y fortaleciendo su cuerpo sin efectos secundarios, permitiéndole disfrutar de una vida sin limitaciones y mejorando su bienestar general.",
    domainImgUrl: "https://i.ibb.co/C3C22Ks1/med-Artritis.jpg",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparaartritis.com"
  },
  {
    domainName: ["www.medicinaparabajarpeso.com"],
    domainDescription: "La obesidad es una enfermedad crónica que se origina principalmente por el consumo excesivo de grasas, azúcares y carbohidratos, además de la falta de actividad física. Está relacionada con factores biológicos, sociales, culturales y psicológicos, y su tratamiento debe ser integral, involucrando médicos, nutriólogos, psicólogos y expertos en activación física. Para tratarla, es esencial mejorar la calidad y cantidad de los alimentos consumidos, realizar ejercicio físico, llevar un registro de lo que se come, y evitar el sedentarismo. Además, se recomienda consultar con un profesional de la salud para un control adecuado. En nuestra página, ofrecemos productos ayurvédicos 100% naturales, traídos directamente de la India, que pueden ayudarle en su camino hacia el control de la obesidad de manera efectiva y segura, apoyando su bienestar integral.",
    domainImgUrl: "https://i.ibb.co/Ps0C9bwJ/medbajarpeso.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparabajarpeso.com"
  },
  {
    domainName: ["www.medicinaparacolesterol.com"],
    domainDescription: "En esta página encontrará productos ayurvédicos 100% naturales diseñados para ayudar a controlar el colesterol alto de manera eficaz y segura. Nuestros productos están elaborados con ingredientes originarios de la India, siguiendo procesos milenarios que garantizan su calidad y efectividad. Además, todos nuestros productos cuentan con los certificados necesarios que aseguran su consumo seguro. Si tiene alguna duda o pregunta, no dude en contactarnos por correo y le responderemos a la brevedad. Prasadam es una marca mexicana que ofrece productos ayurvédicos para mejorar su salud y bienestar, incluyendo opciones para controlar el colesterol, bajar de peso y apoyar el manejo de la diabetes.",
    domainImgUrl: "https://i.ibb.co/TBXXCByq/Med-Colesterol.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparacolesterol.com"
  },
  {
    domainName: ["www.medicinaparacruda.com"],
    domainDescription: "HANGOVER es tu solución natural para aliviar los efectos de la resaca y el desvelo. Este suplemento 100% natural está compuesto por ingredientes ayurvédicos como la Ashwagandha y el Amla, conocidos por sus propiedades restauradoras que equilibran el cuerpo, reducen la inflamación y mejoran la digestión.",
    domainImgUrl: "https://i.ibb.co/Ps72G1LR/resaca.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparacruda.com"
  },
  {
    domainName: ["www.medicinaparadepresion.com"],
    domainDescription: "La depresión es una enfermedad caracterizada por una tristeza persistente y la pérdida de interés en las actividades cotidianas, afectando la capacidad para realizar tareas diarias durante al menos dos semanas. Los síntomas incluyen fatiga, cambios en el apetito, alteraciones en el sueño, ansiedad, y sentimientos de inutilidad, entre otros.",
    domainImgUrl: "https://i.ibb.co/7NpQ6NCt/Med-Depresion.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparadepresion.com"
  },
  {
    domainName: ["www.medicinaparadiabetes.com"],
    domainDescription: "Conozca Glufac, su aliado 100% natural para el control de la diabetes. Este suplemento está diseñado para ayudarle a regular los niveles de glucosa y mantener una vida equilibrada. Basado en la medicina ayurvédica, Glufac combina ingredientes poderosos que no solo apoyan el control de la diabetes, sino que también fortalecen el sistema inmunológico y mejoran la digestión. Si busca una solución natural para mantener su salud, Glufac es la opción ideal.",
    domainImgUrl: "https://i.ibb.co/rRd8GSfG/meddiabetes.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparadiabetes.com"
  },
  {
    domainName: ["www.medicinaparagastritis.com"],
    domainDescription: "CIDNI es un suplemento 100% natural inspirado en la medicina ayurvédica, diseñado para brindar alivio efectivo y duradero a quienes sufren de gastritis y otros trastornos estomacales. Su fórmula, que combina extractos de hierbas seleccionadas por sus propiedades digestivas y antiinflamatorias, actúa como un escudo natural contra el reflujo y la irritación estomacal. CIDNI ofrece una solución segura, libre de químicos dañinos, convirtiéndolo en una opción ideal para quienes buscan un enfoque natural para mejorar su salud digestiva.",
    domainImgUrl: "https://i.ibb.co/yccvLp3q/medgastritis.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparagastritis.com"
  },
  {
    domainName: ["www.medicinaparahemorroides.com"],
    domainDescription: "PILOGUARD es un suplemento 100% natural formulado para tratar las hemorroides, inspirado en la medicina ayurvédica. Su fórmula combina extractos de plantas conocidas por sus propiedades antiinflamatorias, astringentes y regenerativas, proporcionando alivio inmediato al dolor, la inflamación y la irritación en la región anal. Además, fortalece el sistema digestivo y vascular, combatiendo tanto los síntomas como las causas subyacentes de las hemorroides. PILOGUARD ofrece una solución natural, segura y libre de químicos agresivos, promoviendo una mejor calidad de vida para quienes buscan un tratamiento eficaz y suave.",
    domainImgUrl: "https://i.ibb.co/4nykzgtC/medHemo.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparahemorroides.com"
  },
  {
    domainName: ["www.medicinaparahigado.com"],
    domainDescription: "LIVAD es un suplemento 100% natural basado en la medicina ayurvédica, formulado con hierbas como Amalaki, Guduchi y Bhringraj, conocidas por sus beneficios para la salud hepática. Este suplemento promueve la desintoxicación, regeneración y protección del hígado sin ingredientes sintéticos ni productos químicos artificiales, lo que lo hace una opción segura y eficaz para quienes buscan apoyar la función hepática de manera natural.",
    domainImgUrl: "https://i.ibb.co/FbLgW3tg/medHig.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.medicinaparahigado.com"
  },
  {
    domainName: ["www.chyawanprash.com.mx"],
    domainDescription: "Chyawanprash es una mermelada negra tradicional de la medicina ayurvédica, con más de 4000 años de historia en la India, elaborada con más de 50 ingredientes naturales activos. Este potente multivitamínico combina hierbas, frutas, y minerales, incluyendo láminas de oro y plata reales, para ofrecer un sabor agridulce único y una serie de beneficios rejuvenecedores para mejorar la calidad de vida. 100% natural, libre de conservadores y químicos, Chyawanprash sigue los procesos ayurvédicos de Rasayana, que promueven la longevidad y el bienestar general, siendo una formulación ideal para revitalizar y fortalecer el cuerpo de manera integral.",
    domainImgUrl: "https://i.ibb.co/7dr66xbv/chyan.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.chyawanprash.com.mx"
  },
  {
    domainName: ["www.mosquitero.com.mx"],
    domainDescription: "Si estás buscando una solución efectiva para protegerte de los mosquitos sin complicaciones, nuestro innovador mosquitero para cama es la respuesta que necesitas. Diseñado para adaptarse perfectamente a cualquier cama, este mosquitero integrado te garantiza noches de descanso reparador, sin esos molestos zumbidos. Ideal para el hogar o de viaje, su diseño plegable y portátil te ofrece comodidad y máxima protección.",
    domainImgUrl: "https://i.ibb.co/tTH68HNg/mosquitero.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.mosquitero.com.mx"
  },
  {
    domainName: ["www.pastaneem.com"],
    domainDescription: "La pasta dental NEEM de PRASADAM está elaborada con extracto de Neem, un árbol originario de la India conocido por sus poderosas propiedades antibacterianas. 100% vegetariana y libre de fluor, esta pasta es ideal para mantener tu higiene bucal de manera natural. Ayuda a eliminar la placa dental, combate el mal aliento, previene las caries al crear una capa protectora sobre los dientes y combate la gengivitis, manteniendo las encías saludables. ",
    domainImgUrl: "https://i.ibb.co/DggwhdN3/pastaneem.png",
    category: "",
    creationDate: "",
    status: "",
    colorDomains: [],
    websiteUrl: "https://www.pastaneem.com"
  },
]);


// Domains for animation in the placeholder bar
const domains = ref([
  "comercioamerica.com",
  "controlcalidad.net",
  "negocioamerica.com",
  "qualitycontrolexports.com",
  "empresasamerica.com",
  "exportacionesamerica.com",
  "exportsamerica.net",
  "harekrishna.com.mx",
  "radhakrishna.com.mx",
  "asafoetida.com.mx",
  "masplacerintimo.com",
  "medicinaparaansiedad.com",
  "medicinaparaartritis.com",
  "medicinaparabajarpeso.com",
  "medicinaparacolesterol.com",
  "medicinaparacruda.com",
  "medicinaparadepresion.com",
  "medicinaparadiabetes.com",
  "medicinaparagastritis.com",
  "medicinaparahemorroides.com",
  "medicinaparahigado.com",
  "chyawanprash.com.mx",
  "mosquitero.com.mx",
  "pastaneem.com",
  "miexpareja.net",
  "mipareja.net",
  "miexnovia.com.mx",
  "miexnovio.com",
  "miexesposa.com",
  "miexesposo.com",
  "balbalatkaar.com",
  "balbalatkar.com",
  "abusadordemenores.com",
  "maltratomenores.com",
  "bullyingestudiantil.com",
  "childrapist.com",
  "asesoradehogar.com",
  "asesorahogar.com",
  "empleadodomestico.com",
  "nanadomestica.com",
  "nanahogar.com",
  "soplete.com.mx",
  "microtorch.com.mx",
  "foredom.com.mx"
]);

// Value for the placeholder that will change for each domain in domains variable
const placeHolderSearch = ref(domains.value[0]);
const toggleDomainPlaceholder = (): void => {
  setInterval(() => {
    placeHolderSearch.value = domains.value[Math.floor(Math.random() * domains.value.length)];
  }, 2000)
}

// const search value for the input
const search = ref('');

// function to search a specific domain
const filterDomains = (): Array<IWebsite> => websites.value = websitesOriginal.value.filter(e => e.domainName.some(domain => domain.toLowerCase().includes(search.value.toLowerCase())));

// variable to toggle the cards view
const isCards = ref(true);

onMounted(() => {
  toggleDomainPlaceholder();
});
</script>

<style scoped></style>
