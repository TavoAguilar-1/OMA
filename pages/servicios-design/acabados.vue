<template>
  <div>
    <main v-if="service" class="acabados-page">
      <BannerV2 
        title="Acabados" 
        subtitle="Tratamientos térmicos y acabados superficiales para mejorar el rendimiento y la apariencia"
        :buttons="[
          { text: 'Ver Detalles', href: '#detalles', class: 'primary-btn' },
          { text: 'Cotizar', href: '/cotiza', class: 'secondary-btn' }
        ]"
      />
      
      <DetallesMaquinadoCNC />
      <CapacidadesCNC />
      <ProcesosCNC />
      <GaleriaCNC />
      <CTASection 
        title="¿Necesita servicios de acabados y tratamientos de alta calidad?"
        subtitle="Contáctenos hoy mismo para discutir su proyecto y obtener una cotización personalizada."
        buttonText="Solicitar cotización"
        buttonLink="/cotiza"
      />
    </main>
    <div v-else class="loading-container">
      <p>Cargando información del servicio...</p>
    </div>
  </div>
</template>

<script>
import BannerV2 from '../../components/BannerV2.vue'
import DetallesMaquinadoCNC from '../../components/services-components/DetallesMaquinadoCNC.vue'
import CapacidadesCNC from '../../components/services-components/CapacidadesCNC.vue'
import ProcesosCNC from '../../components/services-components/ProcesosCNC.vue'
import GaleriaCNC from '../../components/services-components/GaleriaCNC.vue'
import CTASection from '../../components/common/CTASection.vue'
import { getServiceModel } from '../../services/api'
import ServiceModel from '../../models/ServiceModel'

export default {
  name: 'AcabadosPage',
  components: {
    BannerV2,
    DetallesMaquinadoCNC,
    CapacidadesCNC,
    ProcesosCNC,
    GaleriaCNC,
    CTASection
  },
  head() {
    return {
      title: 'Acabados | OMA - Servicios de Manufactura',
      meta: [
        { hid: 'description', name: 'description', content: 'Servicios de acabados y tratamientos térmicos para piezas metálicas. Ofrecemos anodizado, niquelado, powder coat, black oxide, fosfato y más.' }
      ]
    }
  }
}
</script>

<style scoped>
.acabados-page {
  background-color: var(--background-light);
  min-height: 100vh;
}

html {
  scroll-behavior: smooth;
}
</style>
