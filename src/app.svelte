<script lang="ts">

  import techs from './data/tech-stack.json'
  import projects from './data/projects.json'
  import ProjectView from './components/project-view.svelte';
  import Contact from './components/contact.svelte'
  import DownloadIcon from './assets/icons/download-icon.svelte'

  const CV_LINK = '/docs/001_Maravilla_Jon_Ariel_CV.pdf'

  const viewCV = () => {
    window.open(CV_LINK, '_blank');
  }

</script>

<main>

  <section class="hero">
    <h1>JON ARIEL MARAVILLA</h1>
    <span>Full Stack Developer</span>
    <p>
      Remote full-stack developer based in the Philippines, helping businesses build reliable, user-friendly web applications.
      I focus on scalable architecture, clean code, and continuous learning.
    </p>
    <div class="cta">
      <button 
        id="btn-download-cv" 
        data-umami-event="download-cv" 
        class="btn primary" 
        onclick={viewCV}
        >
        <DownloadIcon />
        DOWNLOAD CV
      </button>
    </div>
  </section>

  <!-- Tech Section -->
   <section>
    <h2>Technologies I Use To Build Stuff</h2>
    <div class="tech-stack">
      {#each techs as tech}
      <div >
         <img src={`https://skillicons.dev/icons?i=${tech.icon}`} alt={`${tech.name} icon`} width="30" height="30">
          {tech.name}
      </div>      
      {/each}
    </div>
   </section>

   <!-- Projects Section -->
  <section>
    <h2>Projects</h2>
    <div class="projects">
      {#each projects as project}
      <ProjectView 
        title={project.title} 
        subtitle={project.subtitle} 
        dateStarted={project.dateStarted} 
        dateEnded={project.dateEnded} 
        description={project.description} 
        tags={project.tags} 
        links={project.links}
        imageSources={project.imageSources} 
        />
      {/each}
    </div>
  </section>

  <Contact 
    email="jonarielm@gmail.com"
    github="https://github.com/jonarielm"
    linkedin="https://linkedin.com/in/jonarielm"
   />

 
</main>

<style>

  main {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
    width: 100%;
    max-width: 1270px;
    margin: 0 auto;
  
  }

  section {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;

    /* dotted bg */
    background-image: radial-gradient(circle 2px at 10px 10px, var(--color-pale-light) 20%, transparent 40%);
    background-size: 20px 20px;

    padding: 2rem;

    &>h2 {
      text-transform: uppercase;
      letter-spacing: 0.1em;
      font-size: large;
      margin-bottom: 1rem;
      background-image: linear-gradient(135deg, var(--color-pale-light-25) 12.5%, transparent 0, transparent 50%, var(--color-pale-light-25) 0, var(--color-pale-light-25) 62.5%, transparent 0, transparent);
      background-size: 5px 5px;
    }
  }

  h1, h2 {
    border-top: 1px solid var(--color-pale-light-25);
    border-bottom: 1px solid var(--color-pale-light-25);
  }

  .hero {

    &>h1 {
    font-size: 2.5rem;
    font-weight: 600;
    color: var(--color-light);
    }
    &>span {
      font-weight: 500;
      font-size: 1.2rem;
      color: var(--color-light);
    }
    &>p {
      max-width: 800px;
      margin: 0.7rem 0;
    }
  }

  .cta {
    display: flex;
    gap: 1rem;
    margin-top: 0.5rem;
  }

  .tech-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 0 1rem;

    &>div {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 0.5rem 1rem;
      background-color: var(--color-pale-light-25);
      color: var(--color-light);
      border-radius: 0.5rem;
      transition: all 0.3s ease;
      border: 1px solid var(--color-light);      
      font-size: medium;
    }
  }

  .projects {
    display: flex;
    flex-direction: column;
    padding: 0 1rem;
    gap: 5rem;
  }

  @media only screen and (max-width: 640px) {
    main {
      padding: 1rem 0;
    }
    section {
      padding: 1rem;
    }

    .hero {
      &>h1 {
        font-size: xx-large;
      }
    }

    .tech-stack {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
      gap: 1rem;
      &>div {
        font-size: small;
      }
    }
  }


</style>
