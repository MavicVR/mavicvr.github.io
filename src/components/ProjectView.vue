<template>
    <section id="our_project">
      <div class="container text-center">
        <h2 class="section-title text-center">Projekt</h2>
  
        <div class="project-info">
          <!-- Buttons to toggle content -->
          <div class="btn-group" role="group" aria-label="Project Info">
            <button
              type="button"
              class="btn"
              :class="{ active: activeButton === 1 }"
              @click="showContent('ausgangslage'), setActiveButton(1)"
            >
              Ausgangslage
            </button>
            <button
              type="button"
              class="btn"
              :class="{ active: activeButton === 2 }"
              @click="showContent('meilensteine'), setActiveButton(2)"
            >
              Meilensteine
            </button>
          </div>
  
          <div class="group-content">
            <div v-if="activeContent === 'ausgangslage'" class="collapse show">
              <p>
                Heutzutage werden Drohnen in allen möglichen Bereichen eingesetzt, wie etwa in der
                Filmindustrie. Allerdings wirkt deren Steuerung anfangs kompliziert und erfordert viel
                Erfahrung, um sie zu meistern. Daher ist eine intuitive Steuerung für Kameradrohnen von
                entscheidender Bedeutung, um konstant qualitativ hochwertige Aufnahmen zu erzielen.
              </p>
            </div>
            <div v-if="activeContent === 'meilensteine'" class="collapse show">
  <table class="milestones-table">
    <thead>
      <tr>
        <th>Datum</th>
        <th>Unser Ziel</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="reach-date">15.10.2023</td>
        <td>Exploration und Machbarkeit durchgeführt.</td>
      </tr>
      <tr>
        <td>28.10.2023</td>
        <td>Erfolgreiche Verbindung zwischen der Drohne und VR-Brille hergestellt.</td>
      </tr>
      <tr>
        <td>12.11.2023</td>
        <td>Erfolgreiche Kamerasteuerung mithilfe der VR-Brille implementiert.</td>
      </tr>
      <tr>
        <td>04.02.2024</td>
        <td>VR-App fertig implementiert und funktionsfähig.</td>
      </tr>
      <tr>
        <td>29.02.2024</td>
        <td>Testphase abgeschlossen.</td>
      </tr>
    </tbody>
  </table>
</div>

            <!-- Add more content sections and use v-if for each -->
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        activeContent: 'ausgangslage', // Initially show Ausgangslage
        activeButton: 1, // Initially set the first button as active
      };
    },
    methods: {
      showContent(content) {
        this.activeContent = content;
      },
      setActiveButton(buttonIndex) {
        this.activeButton = buttonIndex;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Custom styles to match provided fonts and colors */
  section {
    background-color: var(--color-background);
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
    border: 1px solid var(--color-text);
    border-radius: 5px;
  }
  
  .group-content div {
    padding: 1rem;
    border-bottom: 2px solid var(--color-text);
  }
  
  .group-content div p {
    width: 90%;
  }

  .milestones-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

.milestones-table th,
.milestones-table td {
  border: 1px solid var(--color-text);
  padding: 10px;
  text-align: left;
}

.milestones-table th {
  background-color: var(--color-text);
  color: var(--color-white);
}


.milestones-table tbody tr:hover {
  background-color: #f2f2f2;
  color: var(--color-text);
}

  </style>
  