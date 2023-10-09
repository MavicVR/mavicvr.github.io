<template>
  <section id="about_us">
    <div class="container">
      <h2 class="section-title text-center">Über uns</h2>
    </div>

    <div class="container about-us-info">
      <!-- Person 1 -->
      <div class="row justify-content-center">
        <div class="col-md-4">
          <div class="card">
            <img
              src="../assets/img/logo-black.png"
              alt="Bishow Bhattarai"
              class="card-img-top mx-auto d-block"
            />
            <div class="card-body text-center">
              <h3 class="card-title">Bishow Bhattarai</h3>
              <button
                @click="toggleText(1)"
                class="more-user-info"
                data-bs-toggle="tooltip"
                data-bs-placement="top"
                title="Mehr erfahren"
                data-person="1"
              >
                +
              </button>
              <p v-show="showText[1]" class="card-text mt-2 themenstellung">
                Implementierung einer Bibliothek für die effiziente Datenübertragung zwischen der
                DJI-Schnittstelle und einer VR-Brille.
              </p>
            </div>
          </div>
        </div>

        <!-- Person 2 -->
        <div class="col-md-4">
          <div class="card">
            <img
              src="../assets/img/logo-black.png"
              alt="Sergey Proshutinskiy"
              class="card-img-top mx-auto d-block"
            />
            <div class="card-body text-center">
              <h3 class="card-title">Sergey Proshutinskiy</h3>
              <h3 class="user-role">Projektleiter</h3>
              <button
                @click="toggleText(2)"
                class="more-user-info"
                data-bs-toggle="tooltip"
                data-bs-placement="top"
                title="Mehr erfahren"
                data-person="2"
              >
                +
              </button>

              <p v-show="showText[2]" class="card-text mt-2 themenstellung">
                Entwicklung einer Schnittstelle für die Kommunikation zwischen einer DJI-Drohne und
                einer VR-Brille.
              </p>
            </div>
          </div>
        </div>

        <!-- Person 3 -->
        <div class="col-md-4">
          <div class="card">
            <img
              src="../assets/img/logo-black.png"
              alt="Marco Steinberger"
              class="card-img-top mx-auto d-block"
            />
            <div class="card-body text-center">
              <h3 class="card-title">Marco Steinberger</h3>
              <button
                @click="toggleText(3)"
                class="more-user-info"
                data-bs-toggle="tooltip"
                data-bs-placement="top"
                title="Mehr erfahren"
                data-person="3"
              >
                +
              </button>

              <p v-show="showText[3]" class="card-text mt-2 themenstellung">
                Entwicklung einer benutzerfreundlichen VR-App für die Steuerung einer Drohne und
                deren Kamera.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      showText: {
        1: false,
        2: false,
        3: false
      }
    }
  },
  methods: {
    toggleText(personNumber) {
      // Toggle the visibility of text for the selected person
      this.showText[personNumber] = !this.showText[personNumber]

      // Get the button element for the selected person
      const buttonElement = document.querySelector(`button[data-person="${personNumber}"]`)

      // Check if the text is visible and update the button text accordingly
      if (this.showText[personNumber]) {
        buttonElement.innerHTML = '-'
      } else {
        buttonElement.innerHTML = '+'
      }
    }
  }
}
</script>

<style scoped>
.about-us-info {
  margin-top: 120px;
}

button.more-user-info {
  background-color: var(--color-background);
  border: none;
  color: var(--color-white);
  font-size: 1.5rem;
  font-family: 'Lato-Black', sans-serif;
  cursor: pointer;
  margin-top: 15px;
  padding: 2px 15px;
  border-radius: 5px;
}

.card {
  border: none;
  border-radius: 5px;
  margin-bottom: 30px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.6);
  min-height: 400px;
}

.card:hover {
  transform: scale(1.01);
}

.card img {
  border-radius: 50%;
  width: 200px;
}

h3.user-role {
  font-size: 1.2rem;
  font-family: 'Lato-Bold', sans-serif;
  color: var(--color-text);
}

.card-text.themenstellung {
  font-size: 1rem;
  font-family: 'Lato-Regular', sans-serif;
}
.card-text.themenstellung::before {
  content: 'Themenstellung: ';
  font-family: 'Lato-Bold', sans-serif;
}
</style>
