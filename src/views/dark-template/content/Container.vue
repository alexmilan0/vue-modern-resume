<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="¿Quien soy?"
      >
        Soy Licenciada en Comunicación Social nacida en Venezuela 
		*/<a href="http://delix.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=delix">Delix.ir</a>, <a href="https://bytegate.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=bytegate">Bytegate.ir</a> and <a href="http://bobet.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=bobet">Bobet.ir</a> and co-founder of <a href="https://smo.li/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=smoli">Smo.li</a>.<br>/*
        Desde que empecé a desarrollar mi carrera profesional mi objetivo ha sido centrarme en el área que engloba la comunicación digital y el desarrollo de estrategias para el buen funcionamiento de una marca o empresa..
		Me desempeñé varios años como Social Media Manager trabajando de la mano del departamento comercial y donde actualmente pertenezco como Account Manager. Soy Creativa, pro- activa, optimista y apasionada. Estoy buscando crecimiento profesional y potenciar mi carrera. 
	  </content-section>
      <content-section
        v-if="prouds"
        title="Algunos de mis Goals"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-help-rhombus-outline',
        text  : 'Manejo de clientes internacionales!',
      },
      {
        icon  : 'mdi-library-music',
        text  : 'No temo a trabajar bajo presión',
      },
      {
        icon  : 'mdi-timer-sand',
        text  : 'Me adapto rápidamente a los cambios y me manejo bien bajo presión',
      },
      {
        icon  : 'mdi-account-multiple',
        text  : 'No le temo a la toma de decisiones',
      },
    ],
    educations: [
      {
        from       : '2010',
        to         : '2015',
        title      : 'Licenciada en Comunicación Social',
        location   : 'Universidad Santa María',
      },
    ],
    skills: [
      {
        title: 'Photoshop',
        icon : 'mdi-language-php',
        value: 95,
      },
      {
        title: 'Illustrator',
        icon : 'mdi-language-javascript',
        value: 80,
      },
      {
        title: 'Indesign',
        icon : 'mdi-laravel',
        value: 90,
      },
      {
        title: 'Facebook ads',
        icon : 'mdi-vuejs',
        value: 90,
      },
      { divider: true },
      {
        title: 'Instagram',
        icon : 'mdi-ubuntu',
        value: 70,
      },
      {
        title: 'Wordpress',
        icon : 'mdi-linux',
        value: 47,
      },
      {
        title: 'Google Analytics',
        icon : 'mdi-shield-lock',
        value: 80,
      },
      {
        title: 'Mailchimp',
        icon : 'mdi-test-tube',
        value: 26,
      },
      {
        title: 'SEO/SEM',
        icon : 'mdi-truck-fast',
        value: 35,
      },
      {
        title: 'Ecommerce',
        icon : 'mdi-git',
        value: 67,
      },
      { divider: true },
      {
        title: 'Estrategias digitales',
        icon : 'mdi-chip',
        value: 29,
      },
      {
        title: 'C/C++',
        icon : 'Metricool',
        value: 38,
      },
      { divider: true },
      {
        title: 'Leadership',
        icon : 'mdi-account-group',
        value: 90,
      },
      {
        title: 'Content Marketing (+340 articles)',
        icon : 'mdi-text',
        value: 96,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
