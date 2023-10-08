<template>
    <NavbarView />
    <section id="hero">
        <div class="hero-container text-center" ref="heroContainer">
            <div class="drone" ref="drone"></div>
            <div class="landing-header">
                <span class="word">Ma</span>
                <span class="word">vu</span>
                <span class="word">lus</span>
            </div>
            <div class="down-arrow">
                <a href="#about_us"><img src="../assets/img/arrow-down.svg" alt="down arrow" width="60" /></a>
            </div>
        </div>
    </section>

    <!-- About section-->
    <AboutUsView />

    <!-- Project section-->
    <ProjectView />
</template>
  
<script>
import NavbarView from './NavbarView.vue';
import AboutUsView from './AboutUsView.vue';
import ProjectView from './ProjectView.vue';

export default {
    name: 'HomeView',
    components: {
        NavbarView,
        AboutUsView,
        ProjectView,
    },
    data() {
        return {
            isFirstMouseMovement: true,
        };
    },
    mounted() {
        this.followMouseDrone();
    },
    methods: {
        followMouseDrone() {
            const heroContainer = this.$refs.heroContainer;
            const drone = this.$refs.drone;


            heroContainer.addEventListener('mousemove', (e) => {
                const containerRect = heroContainer.getBoundingClientRect();
                const mouseX = e.clientX - containerRect.left;
                const mouseY = e.clientY - containerRect.top;

                if (this.isFirstMouseMovement) {
                    // Animate drone to the new position
                    drone.style.transition = 'all 0.5s ease-in-out';
                    this.isFirstMouseMovement = false;
                } else {
                    // Don't animate for subsequent moves
                    drone.style.transition = 'none';
                }

                // Update drone position based on mouse coordinates
                drone.style.left = mouseX + 'px';
                drone.style.top = mouseY + 'px';
            });


            heroContainer.addEventListener('mouseleave', () => {

                // Reset drone position with an animation to the bottom right corner
                drone.style.left = '80%';
                drone.style.top = '70%';
                drone.style.transition = 'all 0.5s ease-in-out';
                this.isFirstMouseMovement = true;
            });
        },
    },
};
</script>

<style lang="scss" scoped>
.hero-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 150px;
    position: relative;
    z-index: 1;
}

.drone {
    z-index: 0;
    background-image: url(../assets/img/drone-flying.svg);
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    width: 180px;
    height: 180px;
    position: absolute;
    top: 70%;
    left: 80%;
    opacity: 0.5;
}

.landing-header {
    z-index: 1;
    font-size: 10rem;
    font-family: 'Lato-Black', sans-serif;
    color: var(--color-white);
    margin-top: 100px;
    letter-spacing: 10px;

    .word {
        margin-bottom: 10px; // Adjust the spacing between parts
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
  