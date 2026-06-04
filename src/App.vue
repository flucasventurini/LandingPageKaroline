<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'

import logoGold from '../assets/PNG .png'
import logoWhite from '../assets/PNG Branco.png'
import portrait from '../assets/foto nova ka.jpg'
import officePortrait from '../assets/Advogada de Família.jpeg'
import serviceMark from '../assets/Screenshot_20230809_132714_Canva-removebg-preview.png'

const whatsappUrl = 'https://wa.me/message/CPRZ3EYMI5BWB1'

const navItems = [
  { label: 'Início', href: '#home' },
  { label: 'Atuação', href: '#services' },
  { label: 'Sobre', href: '#about' },
  { label: 'Benefícios', href: '#benefits' },
  { label: 'Contato', href: '#contact' },
]

const services = [
  {
    title: 'Divórcio / Separação',
    description:
      'Põe fim ao casamento. Define a partilha dos bens, pensão alimentícia, guarda, visitas aos filhos, nome de casado e altera o estado civil.',
  },
  {
    title: 'Direito das Famílias',
    description:
      'Regula os relacionamentos familiares no momento do casamento, divórcio e união estável. Direitos patrimoniais e relações com os filhos de guarda, pensão alimentícia e convivência.',
  },
  {
    title: 'Sucessões',
    description:
      'Transfere o patrimônio de pessoas que faleceram para seus herdeiros legais e para aqueles que foram beneficiados por testamento.',
  },
]

const benefits = [
  {
    kicker: '01',
    title: 'Atendimento facilitado',
    description: 'Entre em contato por WhatsApp sem burocracia.',
  },
  {
    kicker: '02',
    title: 'Experiência',
    description: 'Advogada com ampla experiência em Direito das Famílias e Sucessões.',
  },
  {
    kicker: '03',
    title: 'Transparência',
    description: 'Você será informado acerca de todo andamento do processo.',
  },
  {
    kicker: '04',
    title: 'Contato direto',
    description:
      'Você terá contato direto com a Advogada pelo WhatsApp para tirar dúvidas sempre que necessário.',
  },
]

const trustItems = [
  { label: 'OAB/SP', value: '483.695' },
  { label: 'Atuação', value: 'Famílias e Sucessões' },
  { label: 'Atendimento', value: 'Humanizado' },
]

const heroNotes = [
  {
    title: 'Direito de Família',
    description: 'Divórcio, guarda e alimentos',
  },
  {
    title: 'Sucessões',
    description: 'Inventário e planejamento familiar',
  },
  {
    title: 'Atendimento humanizado',
    description: 'Clareza, acolhimento e orientação',
  },
]

const menuOpen = ref(false)
const scrolled = ref(false)
const showTop = ref(false)
const currentYear = computed(() => new Date().getFullYear())

function updateScrollState() {
  scrolled.value = window.scrollY > 18
  showTop.value = window.scrollY > 560
}

function closeMenu() {
  menuOpen.value = false
}

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  updateScrollState()
  window.addEventListener('scroll', updateScrollState, { passive: true })
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', updateScrollState)
})
</script>

<template>
  <header class="site-header" :class="{ 'site-header--solid': scrolled }">
    <a class="brand" href="#home" aria-label="Ir para o início" @click="closeMenu">
      <img :src="logoGold" alt="Karoline Correia Carreira Advogada" />
    </a>

    <button
      class="menu-button"
      type="button"
      :aria-expanded="menuOpen"
      aria-label="Abrir menu"
      @click="menuOpen = !menuOpen"
    >
      <span></span>
      <span></span>
    </button>

    <div class="nav-wrap" :class="{ 'nav-wrap--open': menuOpen }">
      <nav class="nav-links" aria-label="Navegação principal">
        <a v-for="item in navItems" :key="item.href" :href="item.href" @click="closeMenu">
          {{ item.label }}
        </a>
      </nav>
      <a class="header-cta" :href="whatsappUrl" target="_blank" rel="noreferrer">
        Agendar consulta
      </a>
    </div>
  </header>

  <main>
    <section id="home" class="hero">
      <div class="hero-copy">
        <p class="eyebrow">Advocacia familiar em Piracicaba-SP</p>
        <h1>
          Soluções jurídicas para famílias com
          <span>clareza e acolhimento</span>
        </h1>
        <p class="hero-lead">
          Advogada especialista em Direito das Famílias e Sucessões para orientar divórcio,
          guarda, alimentos, inventário e demandas familiares de forma humanizada.
        </p>

        <div class="hero-actions">
          <a class="button button--primary" :href="whatsappUrl" target="_blank" rel="noreferrer">
            Falar com especialista
          </a>
          <a class="button button--secondary" href="#about">Conhecer a advogada</a>
        </div>

        <div class="trust-strip" aria-label="Informações de confiança">
          <div v-for="item in trustItems" :key="item.label">
            <strong>{{ item.value }}</strong>
            <span>{{ item.label }}</span>
          </div>
        </div>
      </div>

      <div class="hero-visual" aria-label="Dra. Karoline Correia Carreira em escritório">
        <div class="orb orb--large"></div>
        <div class="orb orb--small"></div>
        <div class="dot-grid" aria-hidden="true"></div>
        <figure>
          <img :src="officePortrait" alt="Dra. Karoline Correia Carreira em seu escritório" />
        </figure>
        <div class="floating-notes" aria-label="Áreas e diferenciais do atendimento">
          <div
            v-for="(note, index) in heroNotes"
            :key="note.title"
            class="floating-note"
            :class="`floating-note--${index + 1}`"
          >
            <span>{{ note.title }}</span>
            <strong>{{ note.description }}</strong>
          </div>
        </div>
      </div>
    </section>

    <section id="services" class="services">
      <div class="section-heading">
        <p class="eyebrow">Áreas de atuação</p>
        <h2>Atuação precisa para decisões familiares e patrimoniais sensíveis.</h2>
      </div>

      <div class="services-grid">
        <article v-for="service in services" :key="service.title" class="service-card">
          <img :src="serviceMark" alt="" />
          <span>Atuação</span>
          <h3>{{ service.title }}</h3>
          <p>{{ service.description }}</p>
        </article>
      </div>
    </section>

    <section id="about" class="about">
      <div class="about-media">
        <img :src="portrait" alt="Dra. Karoline Correia Carreira" />
      </div>

      <div class="about-content">
        <p class="eyebrow">Sobre a advogada</p>
        <h2>Dra. Karoline Correia Carreira</h2>
        <p class="oab">OAB/SP nº 483.695</p>
        <p>
          Advogada que atua exclusivamente na área de Direito das Famílias e Sucessões. Possui
          vasta experiência em ações de fixação de alimentos, regulamentação de guarda e convivência
          e execução de alimentos.
        </p>
        <p>
          Pós-graduada em Direito das Famílias e Sucessões pelo IBDFAM - Instituto Brasileiro de
          Direito de Família e atualmente pós-graduanda em LLM Direito Civil na USP-RP. Atuou por 2
          anos junto ao Ministério Público exclusivamente na Vara de Família e Sucessões.
        </p>
      </div>
    </section>

    <section id="benefits" class="benefits">
      <div class="section-heading section-heading--center">
        <p class="eyebrow">Benefícios</p>
        <h2>Um acompanhamento próximo para transformar incerteza em direção.</h2>
      </div>

      <div class="benefits-grid">
        <article v-for="benefit in benefits" :key="benefit.title" class="benefit-card">
          <span>{{ benefit.kicker }}</span>
          <h3>{{ benefit.title }}</h3>
          <p>{{ benefit.description }}</p>
        </article>
      </div>
    </section>

    <section id="contact" class="contact">
      <div class="contact-panel">
        <img :src="logoWhite" alt="Karoline Correia Carreira Advogada" />
        <p class="eyebrow">Contato</p>
        <h2>Pronto para resolver sua questão familiar?</h2>
        <p>Entre em contato conosco e agende sua consulta.</p>
        <a class="button button--primary" :href="whatsappUrl" target="_blank" rel="noreferrer">
          Falar com especialista
        </a>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div>
      <strong>Dra. Karoline Correia Carreira</strong>
      <span>Especialista em Direito das Famílias e Sucessões</span>
    </div>
    <div>
      <span>Rua Voluntários de Piracicaba, nº 1105, Cidade Alta, Piracicaba-SP</span>
      <span>© {{ currentYear }} Karoline Correia Carreira</span>
    </div>
  </footer>

  <a class="whatsapp-float" :href="whatsappUrl" target="_blank" rel="noreferrer" aria-label="Falar pelo WhatsApp">
    <svg viewBox="0 0 32 32" aria-hidden="true">
      <path
        fill="currentColor"
        d="M16.01 3.2A12.72 12.72 0 0 0 5.02 22.3L3.2 28.8l6.65-1.74a12.72 12.72 0 0 0 6.16 1.57h.01A12.72 12.72 0 0 0 16.01 3.2Zm0 23.24h-.01a10.52 10.52 0 0 1-5.36-1.47l-.38-.23-3.95 1.03 1.05-3.84-.25-.4a10.49 10.49 0 1 1 8.9 4.91Zm5.76-7.85c-.32-.16-1.87-.92-2.16-1.03-.29-.11-.5-.16-.71.16-.21.32-.81 1.03-.99 1.24-.18.21-.37.24-.68.08-.32-.16-1.34-.49-2.55-1.57-.94-.84-1.58-1.88-1.76-2.2-.18-.32-.02-.49.14-.65.14-.14.32-.37.47-.55.16-.18.21-.32.32-.53.11-.21.05-.4-.03-.55-.08-.16-.71-1.71-.97-2.34-.26-.62-.52-.54-.71-.55h-.61c-.21 0-.55.08-.84.4-.29.32-1.1 1.08-1.1 2.63s1.13 3.05 1.29 3.26c.16.21 2.22 3.39 5.38 4.75.75.32 1.34.52 1.8.67.76.24 1.45.21 2 .13.61-.09 1.87-.76 2.14-1.5.26-.74.26-1.37.18-1.5-.08-.13-.29-.21-.61-.37Z"
      />
    </svg>
  </a>

  <button
    class="back-to-top"
    :class="{ 'back-to-top--visible': showTop }"
    type="button"
    aria-label="Voltar ao topo"
    @click="scrollToTop"
  >
    ↑
  </button>
</template>
