<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'Mis Experiencias'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        year : '2020- Presente',
        title: 'Account Manager - Coarts S.A',
        html : `
				<p>
				Analizar y gestionar cartera de clientes.
				</p>
				<p>
				Mejorar la comunicación con el cliente.
				</p>
				<p>
				Velar por que lo RO sean positivos.
				</p>
				<p>
				Cumplir y velar con los objetivos de ventas.
				<p>
				Apoyar y hacer seguimiento de departamento operativo en el cumplimiento de las funciones.
				</p>
				<p> 
				Solucionar y canalizar la resolución del inconveniente al cliente.
				</p>
				<p>
				Fidelización con los actuales clientes y expansión de servicios.
				</p>
				<p>
				A cargo 6 personas.
				</p>,
      },
      {
        detailed   : true,
        year       : 'Jul 2018 - Oct 2020',
        transparent: true,
        title      : 'Marketing Digital - Content Creator',
        /* eslint-disable no-useless-escape */
        html       : `
		
				<p>
				Definir la identidad corporativa de la Cia.
				</p>
				<p>
				Emitir reportes mensuales al directorio.
				</p>
				<p>
				Diseño de plan de la comunicación interna.
				</p>
				<p>
				Producción de piezas de comunicación interna y externa, revistas para empleados, informes anuales, folletos corporativos, etc.
				</p>
				<p>Creación, mantenimiento y actualización de los portales de comunicación internos y externos, incluyendo comunicados, páginas web y redes
sociales. <p> 
                `,
        /* eslint-enable no-useless-escape */
        icon: 'mdi-worker',
      },
      {
        year       : 'Mayo 2015 - Junio 2016',
        transparent: true,
        title      : 'Social Media Manager',
        html       : `
          <p>
           Coordinación del área de marketing online (incluyendo página web, posicionamiento SEO/SEM, Social Media, etc)
          </p>
          <p>
		  Estrategia, generación y análisis de campañas de email marketing.
          </p>
          <p>
		  Apoyo al departamento comercial en la generación de leads enfocados a la conversión.
          </p>
          <p>
		  Creación de contenidos. Nivel medio en herramientas de diseño vectorial: Photoshop, Illustrator.
          </p>
		  <p>
		  Creación, Mantenimiento y actualización de los diferentes catálogos online.
          </p>
        `,
        image    : 'img/timeline/wifi-shield.png',
        iconImage: 'img/timeline/wifi-shield-icon.png',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
