<template>
  <div class="loading-container" v-if="!isLoaded">
    <div class="loading-bar">
      <div class="loading-bar__letter" v-for="(letter, index) in letters" :key="index">
        <transition name="loading-bar__letter">
          <div v-if="showLetter(index)" class="loading-bar__letter-inner">
            {{ letter }}
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<style scoped>
.loading-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  background-color: white;
  top: 0;
  left: 0;
  color: var(--color-text);
  z-index: 999;
  position: fixed;
}

.loading-bar {
  display: flex;
  justify-content: center;
  align-items: center;
}

.loading-bar__letter {
  margin: 0 5px;
}

.loading-bar__letter-inner {
  transform: scale(1);
  transition: transform 0.5s ease-in-out;
}

.loading-bar__letter-enter-active {
  transform: scale(1);
}

.loading-bar__letter-leave-active {
  transform: scale(0);
}

.loading-bar__letter {
  font-size: 3rem;
  font-family: 'Lato-Black', sans-serif;
}
</style>

<script>
export default {
  data() {
    return {
      letters: ['ma', 'view', 'lus'],
      currentIndex: 0,
      isLoaded: false
    }
  },
  methods: {
    showLetter(index) {
      return index === this.currentIndex
    },
    nextLetter() {
      this.currentIndex = (this.currentIndex + 1) % this.letters.length
    }
  },
  mounted() {
    setInterval(() => {
      this.nextLetter()
    }, 900)
    document.onreadystatechange = () => {
      if (document.readyState === 'complete') {
        this.isLoaded = true
      }
    }
  }
}
</script>
