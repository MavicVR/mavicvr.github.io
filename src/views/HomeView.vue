<template>
    <NavbarView />
  
    <!-- Hero section-->
    <section id="hero">
      <div class="hero-container text-center">
        <DroneComponent />
        <div class="landing-header">
          <span class="word">Ma</span>
          <span class="word">vu</span>
          <span class="word">lus</span>
        </div>
        <div class="slogan-container">
          <p class="pronunciation">[maːviewːlus]</p>
          <p class="slogan">VR Drohnesteuerung</p>
        </div>
        <div class="down-arrow">
          <a href="#about_us"><img src="../assets/img/arrow-down.svg" alt="down arrow" width="60" /></a>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import NavbarView from '../components/NavbarComponent.vue';
  import DroneComponent from '../components/DroneComponent.vue';
  
  export default {
    name: 'HomeView',
    components: {
      NavbarView,
      DroneComponent,
    },
    mounted() {
      this.moveDrone(); // Set up the event listener
    },
    methods: {
      moveDrone() {
        const drone = document.querySelector('.drone');
        const maxX = window.innerWidth - drone.clientWidth;
        const maxY = window.innerHeight - drone.clientHeight;
  
        document.addEventListener('mousemove', (e) => {
          const x = e.clientX - drone.clientWidth / 2;
          const y = e.clientY - drone.clientHeight / 2;
  
          const adjustedX = Math.min(maxX, Math.max(0, x));
          const adjustedY = Math.min(maxY, Math.max(0, y));
  
          drone.style.transition = 'all 0.1s ease-in';
          drone.style.left = adjustedX + 'px';
          drone.style.top = adjustedY + 'px';
        });
      },
    },
  };
  </script>

<style scoped>
.hero-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 150px;
    position: relative;
    z-index: 1;
}


.slogan{
    font-family: 'Lato-Black', sans-serif;
    font-size: 2.4rem;
    margin-top: 10px;
}
.landing-header {
    z-index: 1;
    font-size: 10rem;
    font-family: 'Lato-Black', sans-serif;
    color: var(--color-white);
    margin-top: 100px;
    letter-spacing: 10px;

    .word {
        margin-bottom: 10px;
        cursor: pointer;
    }
}

.pronunciation {
    color: var(--color-text);
    font-family: 'Lato-Bold', sans-serif;

    span {
        font-style: italic;
        font-size: 1.4rem;
        padding: 0 5px;
        display: inline;
    }
}

.down-arrow {
    margin-top: 13%;
    z-index: 1;
}

.down-arrow a img:hover {
    transform: scale(1.1);
    color: var(--color-text);
}

@media (max-width: 768px) {


    .landing-header {
        font-size: 6.5rem;
    }

    .down-arrow {
        margin-top: 29%;
    }


}

@media (max-width: 576px) {
    .landing-header {
        font-size: 5rem;
    }

    .down-arrow {
        margin-top: 30%;
    }
}

@media (max-width: 400px) {
    .landing-header {
        font-size: 3.5rem;
    }

    .down-arrow {
        margin-top: 35%;
    }
}
</style>
