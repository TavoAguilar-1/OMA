<template>
  <div>
    <main class="industry-page">
      <BannerV3 
        :title="industry.banner.title" 
        :subtitle="industry.banner.subtitle"
        :buttons="industry.banner.buttons"
      />
      
      <DetallesIndustria 
        :titlePrefix="industry.details.titlePrefix"
        :titleHighlight="industry.details.titleHighlight"
        :description="industry.details.description"
        :features="industry.details.features"
        :imageUrl="industry.details.imageUrl"
      />
      
      <CapacidadesIndustria 
        :titlePrefix="industry.capabilities.titlePrefix"
        :titleHighlight="industry.capabilities.titleHighlight"
        :description="industry.capabilities.description"
        :capacities="industry.capabilities.capacities"
      />
      
      <ProcesosIndustria 
        :titlePrefix="industry.process.titlePrefix"
        :titleHighlight="industry.process.titleHighlight"
        :description="industry.process.description"
        :steps="industry.process.steps"
        :commitmentTitle="industry.process.commitmentTitle"
        :commitments="industry.process.commitments"
      />
      
      <GaleriaIndustria 
        :titlePrefix="industry.gallery.titlePrefix"
        :titleHighlight="industry.gallery.titleHighlight"
        :description="industry.gallery.description"
        :showMoreButtonText="industry.gallery.showMoreButtonText"
        :galleryItems="industry.gallery.galleryItems"
        :galleryCategories="industry.gallery.galleryCategories"
      />
      
      <CTASection 
        :title="industry.cta.title"
        :subtitle="industry.cta.subtitle"
        :buttonText="industry.cta.buttonText"
        :buttonLink="industry.cta.buttonLink"
      />
    </main>
  </div>
</template>

<script>
import BannerV3 from '../../components/BannerV3.vue'
import DetallesIndustria from '../../components/industrias-components/DetallesIndustria.vue'
import CapacidadesIndustria from '../../components/industrias-components/CapacidadesIndustria.vue'
import ProcesosIndustria from '../../components/industrias-components/ProcesosIndustria.vue'
import GaleriaIndustria from '../../components/industrias-components/GaleriaIndustria.vue'
import CTASection from '../../components/common/CTASection.vue'
import { IndustryModel } from '../../models/IndustryModel'

export default {
  name: 'IndustriaMedica',
  components: {
    BannerV3,
    DetallesIndustria,
    CapacidadesIndustria,
    ProcesosIndustria,
    GaleriaIndustria,
    CTASection
  },
  layout: 'industry',
  pageTransition: {
    name: 'fade-slide-y',
    mode: 'out-in',
    appear: true
  },
  data() {
    return {
      industry: this.getDefaultIndustryData(),
      slug: 'medica'
    }
  },
  methods: {
    getDefaultIndustryData() {
      return {
        banner: {
          title: "Industria Médica",
          subtitle: "Fabricación especializada para dispositivos e instrumentos médicos con altos estándares de calidad",
          buttons: [
            { text: 'Ver Servicios', href: '#servicios', class: 'primary-btn' },
            { text: 'Contáctanos', href: '../contact', class: 'secondary-btn' }
          ]
        },
        details: {
          titlePrefix: "Soluciones para la",
          titleHighlight: "Industria Médica",
          description: "Ofrecemos servicios especializados de manufactura para el sector médico, con altos estándares de calidad y precisión. Nuestros procesos cumplen con los rigurosos requisitos de la industria médica, garantizando la fiabilidad y seguridad de cada componente.",
          features: [
            "Componentes para equipos de diagnóstico",
            "Instrumental médico de precisión",
            "Piezas para equipos de laboratorio",
            "Componentes para dispositivos implantables",
            "Prótesis y componentes ortopédicos"
          ],
          imageUrl: "https://source.unsplash.com/featured/600x400?medical,equipment,healthcare"
        },
        capabilities: {
          titlePrefix: "Nuestras",
          titleHighlight: "Capacidades",
          description: "Contamos con tecnología de punta y personal altamente capacitado para ofrecer soluciones integrales al sector médico.",
          capacities: [
            {
              title: "Mecanizado de alta precisión",
              description: "Fabricación de componentes con tolerancias estrictas para aplicaciones médicas.",
              items: ["Tolerancias micrométricas", "Acabados superficiales de grado médico", "Materiales biocompatibles"]
            },
            {
              title: "Validación y verificación",
              description: "Procesos rigurosos de verificación para garantizar la calidad de los productos médicos.",
              items: ["Inspección dimensional avanzada", "Trazabilidad completa", "Documentación para certificaciones médicas"]
            },
            {
              title: "Fabricación en salas limpias",
              description: "Entorno controlado para la producción de componentes médicos sensibles.",
              items: ["Control de partículas", "Monitoreo ambiental", "Protocolos de esterilidad"]
            }
          ]
        },
        process: {
          titlePrefix: "Nuestro",
          titleHighlight: "Proceso",
          description: "Seguimos un proceso riguroso para garantizar que cada componente cumpla con los estrictos estándares regulatorios del sector médico.",
          steps: [
            {
              title: "Planificación y diseño",
              description: "Evaluamos detalladamente los requisitos técnicos y regulatorios específicos.",
              points: ["Análisis de requerimientos normativos", "Selección de materiales biocompatibles", "Diseño para fabricación"],
              imageUrl: "https://source.unsplash.com/featured/600x400?medical,design"
            },
            {
              title: "Validación de procesos",
              description: "Validamos cada etapa del proceso antes de la producción completa.",
              points: ["Prototipos funcionales", "Pruebas de rendimiento", "Validación de materiales"],
              imageUrl: "https://source.unsplash.com/featured/600x400?laboratory,testing"
            },
            {
              title: "Fabricación y control de calidad",
              description: "Producción en entornos controlados con estrictos protocolos de calidad.",
              points: ["Inspección al 100%", "Documentación completa", "Trazabilidad de materiales"],
              imageUrl: "https://source.unsplash.com/featured/600x400?medical,manufacturing"
            }
          ],
          commitmentTitle: "Nuestro compromiso con la excelencia",
          commitments: [
            {
              title: "Certificaciones médicas",
              description: "Cumplimos con estándares internacionales para la industria médica.",
              icon: "fa-certificate"
            },
            {
              title: "Control de procesos",
              description: "Implementamos controles estrictos para garantizar la consistencia.",
              icon: "fa-check-circle"
            },
            {
              title: "Innovación constante",
              description: "Nos mantenemos a la vanguardia de nuevas tecnologías para el sector médico.",
              icon: "fa-lightbulb"
            }
          ]
        },
        gallery: {
          titlePrefix: "Nuestra",
          titleHighlight: "Galería",
          description: "Explora algunos de nuestros proyectos y componentes fabricados para la industria médica.",
          showMoreButtonText: "Ver Más Proyectos",
          galleryCategories: [
            { id: 'all', name: 'Todos' },
            { id: 'instruments', name: 'Instrumentos' },
            { id: 'implants', name: 'Implantes' },
            { id: 'equipment', name: 'Equipamiento' }
          ],
          galleryItems: [
            {
              title: "Instrumental quirúrgico",
              description: "Herramientas de precisión para procedimientos quirúrgicos.",
              category: "instruments",
              imageUrl: "https://source.unsplash.com/featured/600x400?surgical,instruments"
            },
            {
              title: "Componentes para prótesis",
              description: "Piezas mecanizadas para prótesis de alta durabilidad.",
              category: "implants",
              imageUrl: "https://source.unsplash.com/featured/600x400?prosthetic,medical"
            },
            {
              title: "Equipos de laboratorio",
              description: "Componentes precisos para equipos de análisis clínico.",
              category: "equipment",
              imageUrl: "https://source.unsplash.com/featured/600x400?laboratory,equipment"
            },
            {
              title: "Dispositivos de diagnóstico",
              description: "Piezas para equipos de diagnóstico médico avanzado.",
              category: "equipment",
              imageUrl: "https://source.unsplash.com/featured/600x400?medical,diagnostic"
            },
            {
              title: "Componentes dentales",
              description: "Piezas de precisión para aplicaciones odontológicas.",
              category: "implants",
              imageUrl: "https://source.unsplash.com/featured/600x400?dental,medical"
            },
            {
              title: "Instrumental de precisión",
              description: "Herramientas especializadas para procedimientos delicados.",
              category: "instruments",
              imageUrl: "https://source.unsplash.com/featured/600x400?precision,medical"
            },
            {
              title: "Dispositivos implantables",
              description: "Componentes biocompatibles para implantes médicos.",
              category: "implants",
              imageUrl: "https://source.unsplash.com/featured/600x400?implant,medical"
            },
            {
              title: "Equipos de monitoreo",
              description: "Componentes para sistemas de monitoreo de pacientes.",
              category: "equipment",
              imageUrl: "https://source.unsplash.com/featured/600x400?monitor,medical"
            }
          ]
        },
        cta: {
          title: "¿Listo para comenzar tu proyecto médico?",
          subtitle: "Contáctanos hoy mismo para discutir tus necesidades específicas y obtener una cotización personalizada.",
          buttonText: "Contactar ahora",
          buttonLink: "../contact"
        }
      }
    },
  },
  head() {
    const defaultTitle = 'Industria Médica | OMA - Servicios de Manufactura'
    const defaultDescription = 'Soluciones de manufactura de precisión para la industria médica.'
    
    return {
      title: this.industry?.seo?.title || defaultTitle,
      meta: [
        { hid: 'description', name: 'description', content: this.industry?.seo?.description || defaultDescription }
      ]
    }
  }
}
</script>

<style scoped>
.industry-page {
  padding-top: 0;
  width: 100%;
  margin: 0 auto;
}

/* Page transition animations */
.fade-slide-y-enter-active,
.fade-slide-y-leave-active {
  transition: all 0.5s ease;
}

.fade-slide-y-enter-from {
  opacity: 0;
  transform: translateY(30px);
}

.fade-slide-y-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}

/* Add a subtle animation to the components */
main.industry-page > * {
  animation: fadeInUp 0.7s ease forwards;
  opacity: 0;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Stagger animation for child elements */
main.industry-page > *:nth-child(1) { animation-delay: 0.1s; }
main.industry-page > *:nth-child(2) { animation-delay: 0.2s; }
main.industry-page > *:nth-child(3) { animation-delay: 0.3s; }
main.industry-page > *:nth-child(4) { animation-delay: 0.4s; }
main.industry-page > *:nth-child(5) { animation-delay: 0.5s; }
main.industry-page > *:nth-child(6) { animation-delay: 0.6s; }
</style>
