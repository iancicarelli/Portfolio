<script setup>
import GifSlot from '../components/GifSlot.vue'
import { gifs } from '../data/gifs.js'

const icons = {
  linkedin:
    'M4.98 3.5C3.34 3.5 2 4.85 2 6.5s1.34 3 2.98 3S8 8.15 8 6.5 6.64 3.5 4.98 3.5zM2.4 20.5h5.2V9.3H2.4v11.2zM9.9 20.5h5.2v-5.9c0-3.1 4-3.3 4 0v5.9H24v-7.7c0-6-6.5-5.8-7.8-2.8V9.3H9.9v11.2z',
  github:
    'M12 .8C5.7.8.8 5.9.8 12.3c0 5.1 3.3 9.4 7.9 10.9.6.1.8-.3.8-.6v-2.2c-3.2.7-3.9-1.4-3.9-1.4-.5-1.3-1.2-1.6-1.2-1.6-1-.7.1-.7.1-.7 1.1.1 1.7 1.2 1.7 1.2 1 .1.8 1.8 2.8 1.2.1-.7.4-1.2.7-1.4-2.6-.3-5.3-1.300-5.3-5.8 0-1.3.5-2.4 1.2-3.2-.1-.3-.5-1.5.1-3.1 0 0 1-.3 3.2 1.2.9-.3 1.9-.4 2.9-.4s2 .1 2.9.4c2.2-1.5 3.2-1.2 3.2-1.2.6 1.6.2 2.8.1 3.1.8.8 1.2 1.9 1.2 3.2 0 4.5-2.7 5.5-5.3 5.8.4.3.7.9.7 1.9v2.8c0 .3.2.7.8.6 4.6-1.5 7.9-5.8 7.9-10.9C23.2 5.9 18.3.8 12 .8z',
  mail: 'M2 4h20v16H2V4zm2 2v.01L12 13l8-6.99V6H4zm0 2.83V18h16V8.83l-8 7-8-7z',
  external:
    'M14 3h7v7h-2V6.41l-9.29 9.3-1.42-1.42L17.59 5H14V3zM5 5h5v2H5v12h12v-5h2v5a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2z',
}

const contacts = [
  { label: 'LinkedIn', href: 'https://www.linkedin.com/in/ian-cicarelli-b18200391/', icon: 'linkedin', external: true },
  { label: 'GitHub', href: 'https://github.com/iancicarelli', icon: 'github', external: true },
  { label: 'iancicarelli@gmail.com', href: 'mailto:iancicarelli@gmail.com', icon: 'mail' },
]

const nav = [
  { label: 'Sobre mí', href: '#about' },
  { label: 'Experiencia', href: '#experience' },
  { label: 'Tecnologías', href: '#technologies' },
  { label: 'Proyectos', href: '#projects' },
]

const tickerTop = [
  'Sistema en línea',
  'Disponible para proyectos',
  'ネオ東京 2026',
  'Full Stack // Data // Arquitectura',
  'Universidad de La Frontera',
]

const tickerMid = ['フルスタック', 'FULL STACK', 'データ', 'DATA ENGINEERING', 'アーキテクチャ', 'SOFTWARE ARCHITECTURE']

const jobs = [
  {
    company: 'Globalnet',
    role: 'Desarrollador Frontend',
    date: '2025 – Presente',
    items: [
      'Creación y desarrollo de software integral tipo ERP/CRM.',
      'Toma de requerimientos y diseño de la arquitectura de diferentes módulos del sistema.',
      'Implementación de tablas y filtros dinámicos para la gestión de datos.',
      'Configuración y levantamiento de servicios.',
    ],
    tech: 'Reflex, Python.',
  },
  {
    company: 'Acusmania Ingeniería Acústica',
    role: 'Desarrollador Frontend',
    date: '05/05/2025 – 02/06/2025',
    items: [
      'Creación de wireframes y mockups para el sitio web corporativo.',
      'Desarrollo e implementación de la página web principal.',
    ],
    tech: 'Vue.js, JavaScript, Tailwind CSS.',
  },
  {
    company: 'Comercial Amar Hermanos y Compañía Ltda.',
    role: 'Desarrollador de Software (Práctica Profesional)',
    date: '06/01/2025 – 03/03/2025',
    items: [
      'Desarrollo de aplicaciones empresariales para manejo, procesamiento y análisis de datos.',
      'Aplicación de metodología en cascada para la gestión del ciclo de vida del software.',
      'Participación en la toma y análisis de requerimientos.',
    ],
    tech: 'Java, Python, Tkinter, JavaFX, MySQL.',
  },
]

const devicon = (n) => `https://cdn.jsdelivr.net/gh/devicons/devicon/icons/${n}/${n}-original.svg`
const techs = [
  { name: 'Python', img: devicon('python') },
  { name: 'JavaScript', img: devicon('javascript') },
  { name: 'Java', img: devicon('java') },
  { name: 'Vue.js', img: devicon('vuejs') },
  { name: 'React', img: devicon('react') },
  { name: 'Angular', img: devicon('angular') },
  { name: 'Flutter', img: devicon('flutter') },
  { name: 'Reflex', img: 'https://avatars.githubusercontent.com/u/104714959?s=200&v=4' },
  { name: 'Node.js', img: devicon('nodejs') },
  { name: 'Spring Boot', img: devicon('spring') },
  { name: 'MySQL', img: devicon('mysql') },
  { name: 'PostgreSQL', img: devicon('postgresql') },
  { name: 'MongoDB', img: devicon('mongodb') },
  { name: 'Docker', img: devicon('docker') },
  { name: 'Linux', img: devicon('linux') },
  { name: 'Git', img: devicon('git') },
  { name: 'Figma', img: devicon('figma') },
]

const projects = [
  {
    title: 'Play Lab Integrado',
    desc: 'Portal de juegos inclusivo y accesible fundamentado en reconocimiento de voz y gestos para eliminar barreras de accesibilidad, permitiendo a personas con y sin discapacidades físicas disfrutar de entretenimiento digital interactivo.',
    github: 'https://github.com/iancicarelli/Playlab-Integrado',
    demo: 'https://playlab-integrado.onrender.com/',
    tags: ['Accesibilidad', 'Reconocimiento de voz', 'Gestos', 'Inclusivo', 'Python'],
    gif: gifs.project1,
  },
  {
    title: 'Gestor de Archivos',
    desc: 'Aplicación de escritorio para organizar, administrar y acceder a archivos de forma eficiente, con interfaz gráfica construida en Python.',
    github: 'https://github.com/iancicarelli/Gestor-de-archivos',
    tags: ['Archivos', 'Organizacion', 'Gestion', 'Productividad', 'Utilidad'],
    gif: gifs.project2,
  },
  {
    title: 'Juego JS',
    desc: 'Juego web interactivo construido con JavaScript puro. Proyecto enfocado en lógica de juego, manipulación del DOM y manejo de eventos en el frontend.',
    github: 'https://github.com/iancicarelli/Juegojs',
    tags: ['JavaScript', 'Web', 'Juego', 'Interactivo', 'Frontend'],
    gif: gifs.project3,
  },
  {
    title: 'CinemaScope',
    desc: 'Explorador y catálogo de películas con buscador integrado, construido como aplicación web con enfoque en la experiencia de usuario y consumo de APIs.',
    github: 'https://github.com/iancicarelli/CinemaScope',
    tags: ['Peliculas', 'Catalogo', 'Web', 'Buscador', 'UI'],
    gif: gifs.project4,
  },
]

const pad = (n) => String(n + 1).padStart(2, '0')
</script>

<template>
  <div class="page">
    <div class="scanlines" aria-hidden="true"></div>

    <!-- ===== TICKER SUPERIOR ===== -->
    <div class="ticker" aria-hidden="true">
      <div class="ticker-row">
        <div class="ticker-track">
          <span v-for="n in 2" :key="'a' + n" class="ticker-group">
            <span v-for="t in tickerTop" :key="t">{{ t }} <b>✦</b></span>
          </span>
        </div>
      </div>
      <div class="ticker-row reverse alt">
        <div class="ticker-track">
          <span v-for="n in 2" :key="'b' + n" class="ticker-group">
            <span v-for="t in tickerTop" :key="t">{{ t }} <b>//</b></span>
          </span>
        </div>
      </div>
    </div>

    <!-- ===== NAV ===== -->
    <nav class="nav" id="top">
      <a class="brand" href="#top">IC<small>_</small></a>
      <div class="nav-links">
        <a v-for="(l, i) in nav" :key="l.href" :href="l.href"><em>{{ pad(i) }}</em>{{ l.label }}</a>
      </div>
      <a class="cta" href="#projects">Ver proyectos ↘</a>
    </nav>

    <!-- ===== HERO ===== -->
    <header class="hero">
      <div class="hero-main">
        <p class="status"><span class="dot"></span> Disponible para proyectos — <a href="mailto:iancicarelli@gmail.com">iancicarelli@gmail.com</a></p>
        <p class="eyebrow">// Portafolio — ポートフォリオ</p>
        <h1 class="glitch" data-text="IAN CICARELLI CHIFFELLE">
          <span>Ian</span>
          <span>Cicarelli</span>
          <span class="outline">Chiffelle</span>
        </h1>
        <p class="subtitle">Ingeniero Informático <i>|</i> Computer Engineering Student <i>|</i> Software Developer</p>
        <p class="summary">
          Estudiante de quinto año de Ingeniería Informática en la Universidad de La Frontera. Me especializo en desarrollo Full Stack, ingeniería de datos y arquitectura de software. Cuento con experiencia práctica desde la toma de requerimientos hasta el despliegue, trabajando en equipos multidisciplinarios para construir soluciones de alta calidad.
        </p>
        <div class="hero-meta">
          <a
            v-for="c in contacts"
            :key="c.label"
            class="btn"
            :href="c.href"
            :target="c.external ? '_blank' : null"
            :rel="c.external ? 'noreferrer' : null"
          >
            <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false"><path :d="icons[c.icon]" /></svg>
            <span>{{ c.label }}</span>
          </a>
        </div>
      </div>

      <aside class="hero-side">
        <GifSlot :src="gifs.hero" label="Hero // Akira" code="CH-01 // NEO-TOKYO" ratio="4 / 5" />
        <dl class="syslog">
          <div class="syslog-head"><span>SYSTEM LOG</span><span>v2026</span></div>
          <div><dt>Operador</dt><dd>Ian Cicarelli Chiffelle</dd></div>
          <div><dt>Clase</dt><dd>Full Stack / Data / Arquitectura</dd></div>
          <div><dt>Base</dt><dd>Universidad de La Frontera</dd></div>
          <div><dt>Actual</dt><dd>Globalnet — Frontend</dd></div>
          <div><dt>Estado</dt><dd class="ok">ONLINE ▮</dd></div>
        </dl>
      </aside>
    </header>

    <!-- ===== MARQUEE GRANDE ===== -->
    <div class="marquee-big" aria-hidden="true">
      <div class="ticker-track">
        <span v-for="n in 2" :key="'m' + n" class="ticker-group">
          <span v-for="(t, i) in tickerMid" :key="t" :class="{ jp: i % 2 === 0 }">{{ t }} <b>⚡</b></span>
        </span>
      </div>
    </div>

    <main>
      <!-- ===== SOBRE MÍ ===== -->
      <section id="about" class="section">
        <div class="section-head">
          <span class="idx">01</span>
          <h2>Sobre mí <small>自己紹介</small></h2>
        </div>
        <div class="about-layout">
          <div class="about-text">
            <p class="lead">
              Estudiante de Ingeniería Informática de quinto año en la Universidad de La Frontera, con marcado interés en la arquitectura de software, el desarrollo Full Stack y la automatización. He trabajado en equipos multidisciplinarios, facilitando la obtención clara de requerimientos y una mejor comprensión de los proyectos, manteniendo un enfoque constante en la calidad del trabajo y el cumplimiento de metas.
            </p>
            <div class="about-grid">
              <article class="card wide">
                <h3><span>[A]</span> Perfil Profesional</h3>
                <p>
                  Ingeniero de Software en formación, con un marcado interés en la arquitectura de
                  sistemas y la automatización de procesos. Me motiva el desarrollo de soluciones que
                  aporten orden y eficiencia, transformando requerimientos de negocio en software
                  funcional. Enfocado en las buenas prácticas y la calidad del código, busco integrarme
                  a equipos donde pueda aportar valor técnico mientras sigo perfeccionando mis
                  habilidades en el desarrollo de aplicaciones.
                </p>
              </article>
              <article class="card">
                <h3><span>[B]</span> Educación</h3>
                <p>Universidad de La Frontera</p>
                <p>Ingeniería Informática</p>
                <p class="date">2022 – Presente</p>
                <p>Bachiller en Programación</p>
                <p class="date">Conferido en Diciembre 2024</p>
              </article>
              <article class="card">
                <h3><span>[C]</span> Idiomas</h3>
                <p>Español (Nativo)</p>
                <p>Inglés (Intermedio)</p>
              </article>
            </div>
          </div>
          <GifSlot class="about-gif" :src="gifs.about" label="About // Ghost in the Shell" code="CH-02 // SECTION 9" ratio="1 / 1" />
        </div>
      </section>

      <!-- ===== BANNER GIF ===== -->
      <div class="banner">
        <GifSlot :src="gifs.banner" label="Banner // Blade Runner" code="CH-03 // LOS ANGELES 2019" ratio="21 / 7" />
        <p class="banner-caption">"All those moments will be lost in time..." <span>— ログ記録</span></p>
      </div>

      <!-- ===== EXPERIENCIA ===== -->
      <section id="experience" class="section">
        <div class="section-head">
          <span class="idx">02</span>
          <h2>Experiencia <small>経歴</small></h2>
          <p>Prácticas y proyectos profesionales enfocados en desarrollo y diseño de soluciones.</p>
        </div>
        <div class="exp-layout">
          <div class="timeline">
            <article v-for="(job, i) in jobs" :key="job.company" class="job">
              <div class="job-index">{{ pad(i) }}</div>
              <div class="job-body">
                <div class="job-header">
                  <h3>{{ job.company }}</h3>
                  <span class="date">{{ job.date }}</span>
                </div>
                <span class="role">{{ job.role }}</span>
                <ul>
                  <li v-for="it in job.items" :key="it">{{ it }}</li>
                  <li class="tech"><strong>Tecnologías utilizadas:</strong> {{ job.tech }}</li>
                </ul>
              </div>
            </article>
          </div>
          <GifSlot class="exp-gif" :src="gifs.experience" label="Exp // Evangelion" code="CH-04 // NERV" ratio="3 / 4" />
        </div>
      </section>

      <!-- ===== TECNOLOGÍAS ===== -->
      <section id="technologies" class="section">
        <div class="section-head">
          <span class="idx">03</span>
          <h2>Tecnologías <small>技術</small></h2>
          <p>Stack técnico y herramientas usadas en proyectos académicos y profesionales.</p>
        </div>
        <div class="carousel-wrapper">
          <div class="carousel-track">
            <template v-for="n in 2" :key="'t' + n">
              <div v-for="t in techs" :key="t.name + n" class="tech-card">
                <img :src="t.img" :alt="t.name" />
                <span>{{ t.name }}</span>
              </div>
            </template>
          </div>
        </div>
        <p class="tech-note">&gt; Actualmente profundizando en Docker y Kubernetes.<span class="caret">_</span></p>
      </section>

      <!-- ===== PROYECTOS ===== -->
      <section id="projects" class="section">
        <div class="section-head row">
          <div>
            <span class="idx">04</span>
            <h2>Proyectos <small>作品</small></h2>
          </div>
          <p>Selección de trabajos. Este bloque se muestra al hacer click en “Proyectos”.</p>
        </div>
        <div class="projects-grid">
          <article v-for="(p, i) in projects" :key="p.title" class="project-card">
            <GifSlot :src="p.gif" :label="'Proyecto // ' + p.title" :code="'FILE-' + pad(i)" ratio="16 / 10" />
            <div class="project-body">
              <h3><span>{{ pad(i) }} /</span> {{ p.title }}</h3>
              <p>{{ p.desc }}</p>
              <div class="tags">
                <span v-for="t in p.tags" :key="t">{{ t }}</span>
              </div>
              <div class="project-links">
                <a class="btn small" :href="p.github" target="_blank" rel="noreferrer">
                  <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false"><path :d="icons.github" /></svg>
                  <span>GitHub</span>
                </a>
                <a v-if="p.demo" class="btn small solid" :href="p.demo" target="_blank" rel="noreferrer">
                  <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false"><path :d="icons.external" /></svg>
                  <span>Ver demo</span>
                </a>
              </div>
            </div>
          </article>
        </div>
        <p class="projects-more">
          Para mas proyectos revisar en
          <a href="https://github.com/iancicarelli" target="_blank" rel="noreferrer">github.com/iancicarelli</a>
        </p>
      </section>

      <!-- ===== CONTACTO (GIF FULL-BLEED) ===== -->
      <section class="contact">
        <GifSlot class="contact-bg" :src="gifs.contact" label="Contacto // Cowboy Bebop" code="CH-05 // BEBOP" ratio="auto" />
        <div class="contact-inner">
          <p class="eyebrow">// See you space cowboy...</p>
          <h2>¿Trabajamos<br />juntos?</h2>
          <a class="btn big" href="mailto:iancicarelli@gmail.com">
            <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false"><path :d="icons.mail" /></svg>
            <span>iancicarelli@gmail.com</span>
          </a>
        </div>
      </section>
    </main>

    <!-- ===== FOOTER ===== -->
    <footer class="footer">
      <div class="footer-grid">
        <div>
          <p class="footer-brand">IC_</p>
          <p class="muted">© 2026 Ian Cicarelli Chiffelle</p>
        </div>
        <div class="footer-col">
          <span class="label">Secciones</span>
          <a v-for="l in nav" :key="l.href" :href="l.href">{{ l.label }}</a>
        </div>
        <div class="footer-col">
          <span class="label">Contacto</span>
          <a
            v-for="c in contacts"
            :key="c.label"
            :href="c.href"
            :target="c.external ? '_blank' : null"
            :rel="c.external ? 'noreferrer' : null"
          >{{ c.label }}</a>
        </div>
      </div>
      <p class="footer-status"><span class="dot"></span> node online — 接続中</p>
    </footer>
  </div>
</template>

<style scoped src="./landing.css"></style>
