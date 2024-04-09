<template>
  <div class="milestones-container">
    <div class="milestones-scrollable">
      <div class="milestone" v-for="(milestone, index) in reversedMilestones" :key="index">
        <div class="milestone-box">
          <div class="date">{{ milestone.date }}</div>
          <div class="short-text">{{ milestone.title }}</div>
          <button class="more-info-button" @click="showPopup(index)">Mehr erfahren</button>
        </div>
      </div>

      <!-- Display no milestone progress found if the milestone is empty -->
      <div v-if="reversedMilestones.length === 0" class="milestone">
        <div class="milestone-box">
          <div class="date">Keine Fortschritte gefunden</div>
          <div class="short-text">Es wurden keine Fortschrittseinträge gefunden.</div>
        </div>
      </div>
    </div>

    <Modal
      :show="popupOpen !== null"
      :title="popupOpen !== null ? displayedMilestone.title : ''"
      :date="popupOpen !== null ? displayedMilestone.date : ''"
      :images="popupOpen !== null ? displayedMilestone.images : []"
      :text="popupOpen !== null ? displayedMilestone.shortText : ''"
      @close="closePopup"
    ></Modal>
  </div>
</template>

<script>
import Modal from "@/components/ModalComponent.vue";

export default {
  data() {
    return {
      milestones: [
        {
          date: "28.11.2023",
          title: "Grundlegende VR-App implementiert",
          shortText: "VR-App zum Testen fertiggestellt und App zur Verbindung mit der Drohne funktionsfähig.",
          images: [],
        },
        {
          date: "16.01.2024",
          title: "Schnittstelle und Bibliothek implementiert",
          shortText: "Schnittstelle für die Drohne und das Bibliothek für die Datenübertragung zwischen der Drohne und der VR grundlegend implementiert.",
          images: [],
        },
        {
          date:"16.03.2024",
          title: "Drohneninformationen und Kopfposition Übertragung erfolgreich",
          shortText: "Drohneninformationen und Kopfposition wurden erfolgreich zwischen der Drohne und der VR-Brille übertragen und implementiert."
        },
        {
          date: "26.03.2024",
          title: "Videoübertragung erfolgreich",
          shortText: "Videoübertragung von der Drohne zur VR-Brille erfolgreich übertragen und implementiert.",
        },
        {
          date: "04.04.2024",
          title: "Drohnensteuerung erfolgreich",
          shortText: "Drohnensteuerung mithilfe der VR-Brille erfolgreich implementiert.",
        },
        
      ],
      popupOpen: null,
    };
  },
  components: {
    Modal,
  },
  computed: {
    reversedMilestones() {
      // Reverse the milestones array to display the newest items first
      return [...this.milestones].reverse();
    },
    displayedMilestone() {
      // Return the milestone to display in the modal based on popupOpen index
      let getReversedMilestones = this.reversedMilestones;
      if (this.popupOpen !== null && this.popupOpen < getReversedMilestones.length) {
        return getReversedMilestones[this.popupOpen];
      } else {
        return {};
      }
    },
  },
  methods: {
    showPopup(index) {
      this.popupOpen = index;
    },
    closePopup() {
      this.popupOpen = null;
    },
  },
};
</script>


<style scoped>
.milestone-box {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  padding: 20px;
  margin: 10px;
  transition: transform 0.2s;
}

.milestone-box:hover {
  transform: translateY(-5px);
}

.date {
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 10px;
  color: var(--color-background); /* Define your color variable here */
}

.short-text {
  font-size: 1rem;
  color: var(--color-text); /* Define your color variable here */
  margin-top: 10px;
}

.more-info-button {
  background-color: var(--color-background); /* Define your background color variable */
  border: none;
  color: var(--color-white); /* Define your text color variable */
  font-size: 1rem;
  cursor: pointer;
  padding: 5px 10px;
  border-radius: 5px;
  margin: 10px 0;
}

.milestone-box {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  padding: 20px;
  margin: 10px;
  transition: transform 0.2s;
}

.milestones-scrollable {
  max-height: 400px; /* Set a suitable maximum height */
  overflow-y: auto;
}

.milestone {
  width: 100%;
}

.modal-images {
  max-height: 200px; /* Set a suitable maximum height */
  overflow-y: auto;
}
</style>
