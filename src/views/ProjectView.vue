<template>
  <section id="our_project">
    <div class="container text-center">
      <div class="header">
        <h2 class="section-title text-center">Projekt</h2>
      </div>

      <div class="project-info">
        <!-- Buttons to toggle content -->
        <div class="btn-group" role="group" aria-label="Project Info">
          <button type="button" class="btn" :class="{ active: activeButton === 1 }"
            @click="showContent('ausgangslage'), setActiveButton(1)">
            Ausgangslage
          </button>
          <button type="button" class="btn" :class="{ active: activeButton === 2 }"
            @click="showContent('features'), setActiveButton(2)">
            Features
          </button>
          <button type="button" class="btn" :class="{ active: activeButton === 3 }"
            @click="showContent('meilensteine'), setActiveButton(3)">
            Meilensteine
          </button>

          <button type="button" class="btn" :class="{ active: activeButton === 4 }"
            @click="showContent('milestone-progress'), setActiveButton(4)">
            Unser Fortschritt
          </button>
        </div>

        <div class="group-content">
          <div v-if="activeContent === 'ausgangslage'" class="collapse show">
            <p>
              Heutzutage werden Drohnen in allen möglichen Bereichen eingesetzt, wie etwa in der
              Filmindustrie. Allerdings wirkt deren Steuerung anfangs kompliziert und erfordert viel
              Erfahrung, um sie zu meistern. Daher ist eine intuitive Steuerung für Kameradrohnen
              von entscheidender Bedeutung, um konstant qualitativ hochwertige Aufnahmen zu
              erzielen.
            </p>
          </div>

          <div v-if="activeContent === 'features'" class="collapse show">
            <ul>
              <li class="feature">Flüssiges Live-Stream von einer Drohnenkamera in VR.</li>
              <li class="feature">Kamera- und Drohnensteuerung durch Kopfbewegungen.</li>
              <li class="feature">Alternative Methoden zur Steuerung einer Drohne.</li>

            </ul>
          </div>
          <div v-if="activeContent === 'meilensteine'" class="collapse show">
            <table class="milestones-table">
              <thead>
                <tr>
                  <th>Datum</th>
                  <th>Unser Ziel</th>
                </tr>
              </thead>
              <tbody class="milestones-body">
                <tr>
                  <td class="milestone-date done">15.10.2023</td>
                  <td class="goal-description done">Exploration und Machbarkeit durchgeführt.</td>
                </tr>
                <tr>
                  <td class="milestone-date done">28.10.2023</td>
                  <td class="goal-description done">Erfolgreiche Verbindung zwischen der Drohne und VR-Brille hergestellt.</td>
                </tr>
                <tr>
                  <td class="milestone-date done">12.11.2023</td>
                  <td class="goal-description">Erfolgreiche Kamerasteuerung mithilfe der VR-Brille implementiert.</td>
                </tr>
                <tr>
                  <td class="milestone-date">04.02.2024</td>
                  <td class="goal-description">VR-App fertig implementiert und funktionsfähig.</td>
                </tr>
                <tr>
                  <td class="milestone-date">29.02.2024</td>
                  <td class="goal-description">Testphase abgeschlossen.</td>
                </tr>
              </tbody>
            </table>
          </div>

          <div v-if="activeContent === 'milestone-progress'" class="collapse show">

            <ProgressView />

          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ProgressView from '../components/MilestoneComponent.vue'

export default {
  data() {
    return {
      activeContent: 'ausgangslage',
      activeButton: 1
    }
  },
  components: {
    ProgressView
  },

  methods: {
    showContent(content) {
      this.activeContent = content
    },
    setActiveButton(buttonIndex) {
      this.activeButton = buttonIndex
    },
    checkIfDone() {
     
      // // Get all milestones (.milestones-body)
      //   let milestones = document.querySelectorAll('.milestones-body tr')

      //   console.log(milestones)

      //   // Loop through all milestones
      //   for (let i = 0; i < milestones.length; i++) {
      //     // Get the date of the milestone
      //     let milestoneDate = milestones[i].querySelector('.milestone-date').innerHTML

      //     console.log(milestoneDate)

      //     // Get the current date
      //     let currentDate = new Date()

      //     // Check if the milestone date is in the past
      //     if (new Date(milestoneDate) < currentDate) {
      //       // Add the class "done" to the milestone description
      //       milestones[i].querySelector('.goal-description').classList.add('done')
      //     }
      //   }

      //TODO: Mark milestones as done if the date is in the past automatically
    }
  },
  mounted() {
    this.checkIfDone()
  }
}
</script>

<style scoped>
section {
  background-color: var(--color-background);
}

.container {
  margin-bottom: 10%;
}

.container h2 {
  font-family: 'Lato-Black', sans-serif;
  margin-top: 1rem;
}

.btn {
  background-color: transparent;
  border: 1px solid var(--color-text);
  color: var(--color-white);
}

.btn:hover {
  background-color: transparent;
  background-color: var(--color-text);
}

.collapse.show {
  display: block;
}

.active {
  background-color: var(--color-text);
  color: var(--color-white);
}

.group-content {
  margin-top: 1rem;
  text-align: left;
  border: 3px solid var(--color-text);
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.6);
}

.group-content div {
  padding: 1rem;
}

.group-content div p {
  width: 90%;
}

.goal-description {
  color: var(--color-white);
}

.milestones-table {
  background-color: var(--color-background);
  border-collapse: collapse;
  width: 100%;
  border-radius: 8px;
  overflow: hidden;
  margin-top: 20px;
}

.milestones-table th,
.milestones-table td {
  border: 1px solid var(--color-background);
  padding: 12px;
  text-align: left;
  font-size: 16px;
  color: var(--color-text);
}

.milestones-table th {
  background-color: var(--color-text);
  color: var(--color-white);
  font-weight: bold;
  text-transform: uppercase;
  border-radius: 0;
}

.milestones-table tbody tr {
  transition: background-color 0.3s;
}



.milestones-table tbody tr:hover {
  background-color: var(--color-light-gray);
}

td.goal-description {
  color: var(--color-white);
}

ul {
  list-style-type: none;
  padding: 0;
  font-size: 1.2rem;
}

ul li.feature {
  list-style: none;
  padding-left: 35px;
  background-image: url('../assets/img/listicon.svg');
  background-repeat: no-repeat;
  background-size: 30px;
  padding-top: 20px;

  background-position: 0 20px;
}

.project-info {
  padding-top: 50px;
}

@media (max-width: 520px) {

  .btn-group {
    flex-direction: column;
    width: 100%;
  }

  .btn-group .btn {
    margin-bottom: 10px;
    border-radius: 3px;
  }
}

td.goal-description.done, td.milestone-date.done {
  color: var(--color-text);
  text-decoration: line-through;
}
</style>
