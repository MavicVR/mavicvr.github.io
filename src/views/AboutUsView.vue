<template>
  <section id="about_us">
    <div class="container">
      <div class="header">

        <h2 class="section-title text-center">Über uns</h2>
      </div>

      <div class="about-us-info">
        <!-- Person 1 -->
        <div class="row justify-content-center">
          <div class="col-md-4">
            <div class="card">
              <div class="user-image">
                <img src="../assets/img/users/bbhattarai.jpg" alt="Bishow Bhattarai" class="card-img mx-auto" />
              </div>
              <div class="card-body text-center">
                <h3 class="card-title">Bishow Bhattarai</h3>
                <p class="user-role">Bibliothek Entwickler</p>
                <p class="contact-email"><a href="mailto:bbhattarai@student.tgm.ac.at">bbhattarai@student.tgm.ac.at</a></p>
                <button @click="toggleText(1)" class="more-user-info" data-bs-toggle="tooltip" data-bs-placement="top"
                  title="Mehr erfahren" data-person="1">
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
              <div class="user-image">
                <img src="../assets/img/users/sproshutinskiy.jpg" alt="Sergey Proshutinskiy" class="card-img mx-auto" />
              </div>
              <div class="card-body text-center">
                <h3 class="card-title">Sergey Proshutinskiy</h3>
                <p class="user-role">Projektleiter / Schnittstelle Entwickler</p>
                <p class="contact-email"><a href="mailto:sproshutinskiy@student.tgm.ac.at">sproshutinskiy@student.tgm.ac.at</a></p>
                <button @click="toggleText(2)" class="more-user-info" data-bs-toggle="tooltip" data-bs-placement="top"
                  title="Mehr erfahren" data-person="2">
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
              <div class="user-image">
                <img src="../assets/img/users/msteinberger.jpg" alt="Marco Steinberger" class="card-img mx-auto" />
              </div>
              <div class="card-body text-center">
                <h3 class="card-title">Marco Steinberger</h3>
                <p class="user-role">VR App Entwickler</p>
                <p class="contact-email"><a href="mailto:msteinberger@student.tgm.ac.at">msteinberger@student.tgm.ac.at</a></p>

                <button @click="toggleText(3)" class="more-user-info" data-bs-toggle="tooltip" data-bs-placement="top"
                  title="Mehr erfahren" data-person="3">
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
section {
  padding: 100px 0;
  background-color: var(--color-white);
}

h2.section-title {
  color: var(--color-background);
}

h2.section-title::after {
  background-color: var(--color-background);
}

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

p.user-role {
  font-size: 1rem;
  font-family: 'Lato-Bold', sans-serif;
  color: var(--color-text);
}
p.contact-email a{
  font-size: 1rem;
  font-family: 'Lato-Regular', sans-serif;
  text-decoration: underline;
  color: var(--color-background);
}

.card-text.themenstellung {
  font-size: 1rem;
  font-family: 'Lato-Regular', sans-serif;
}

.card-text.themenstellung::before {
  content: 'Themenstellung: ';
  font-family: 'Lato-Bold', sans-serif;
}



div.user-image {
  width: 200px;
  height: 200px;
  overflow: hidden;
  border-radius: 50%;
  border: 4px solid var(--color-background);
  margin: 10px auto;
}

.user-image img{
  margin-top: -30%;
}

</style>
