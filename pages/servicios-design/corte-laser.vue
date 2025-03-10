<template>
  <div>
    <main v-if="service" class="corte-laser-page">
      <BannerV2 
        :title="service.banner.title" 
        :subtitle="service.banner.subtitle"
        :buttons="service.banner.buttons"
      />
      
      <DetallesServicio 
        :titlePrefix="service.details.titlePrefix"
        :titleHighlight="service.details.titleHighlight"
        :description="service.details.description"
        :featuresTitle="service.details.featuresTitle"
        :features="service.details.features"
        :materialsTitle="service.details.materialsTitle"
        :materialGroups="service.details.materialGroups"
        :otherMaterialsTitle="service.details.otherMaterialsTitle"
        :otherMaterials="service.details.otherMaterials"
        :advantagesTitle="service.details.advantagesTitle"
        :advantages="service.details.advantages"
        :imageUrl="service.details.imageUrl"
      />
      <CapacidadesServicio 
        :titlePrefix="service.capabilities.titlePrefix"
        :titleHighlight="service.capabilities.titleHighlight"
        :description="service.capabilities.description"
        :capacities="service.capabilities.capacities"
      />
      <ProcesosServicio 
        :titlePrefix="service.process.titlePrefix"
        :titleHighlight="service.process.titleHighlight"
        :description="service.process.description"
        :steps="service.process.steps"
        :commitmentTitle="service.process.commitmentTitle"
        :commitments="service.process.commitments"
      />
      <GaleriaServicio 
        :titlePrefix="service.gallery.titlePrefix"
        :titleHighlight="service.gallery.titleHighlight"
        :description="service.gallery.description"
        :showMoreButtonText="service.gallery.showMoreButtonText"
        :galleryItems="service.gallery.galleryItems"
        :galleryCategories="service.gallery.galleryCategories"
      />
      <CTASection 
        :title="service.cta.title"
        :subtitle="service.cta.subtitle"
        :buttonText="service.cta.buttonText"
        :buttonLink="service.cta.buttonLink"
      />
    </main>
    <div v-else class="loading-container">
      <p>Cargando información del servicio...</p>
    </div>
  </div>
</template>

<script>
import BannerV2 from '../../components/BannerV2.vue'
import DetallesServicio from '../../components/services-components/DetallesServicio.vue'
import CapacidadesServicio from '../../components/services-components/CapacidadesServicio.vue'
import ProcesosServicio from '../../components/services-components/ProcesosServicio.vue'
import GaleriaServicio from '../../components/services-components/GaleriaServicio.vue'
import CTASection from '../../components/common/CTASection.vue'
import { getServiceModel } from '../../services/api'
import ServiceModel from '../../models/ServiceModel'

export default {
  name: 'CorteLaserPage',
  components: {
    BannerV2,
    DetallesServicio,
    CapacidadesServicio,
    ProcesosServicio,
    GaleriaServicio,
    CTASection
  },
  data() {
    return {
      service: null,
      loading: true,
      error: null
    }
  },
  async fetch() {
    try {
      // Get the service slug from the page name
      const slug = 'corte-laser'
      
      // Fetch service data from Strapi
      this.service = await getServiceModel(slug)
      
      // If no data is returned, use default data
      if (!this.service) {
        console.warn('No service data found, using default data')
        this.service = new ServiceModel(ServiceModel.getDefaultData(slug))
      }
    } catch (error) {
      console.error('Error fetching service data:', error)
      this.error = 'Error al cargar los datos del servicio'
      
      // Use default data in case of error
      const slug = 'corte-laser'
      this.service = new ServiceModel(ServiceModel.getDefaultData(slug))
    } finally {
      this.loading = false
    }
  },
  head() {
    if (!this.service) {
      return {
        title: 'Corte Láser | OMA - Servicios de Manufactura',
        meta: [
          { hid: 'description', name: 'description', content: 'Servicios de corte láser de alta precisión para acero, acero inoxidable y aluminio.' }
        ]
      }
    }
    
    return {
      title: this.service.seo.title,
      meta: [
        { hid: 'description', name: 'description', content: this.service.seo.description }
      ]
    }
  }
}
</script>

<style scoped>
.corte-laser-page {
  background-color: var(--background-light);
  min-height: 100vh;
}

.loading-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 50vh;
  font-size: 1.2rem;
  color: var(--text-primary);
}

html {
  scroll-behavior: smooth;
}
</style>
