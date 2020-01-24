<template>
  <div id="app" class="container">
    <div class="container">
      <div v-for="form in forms" :key="form">
        <distanceForm @calculate="addJournalItem" />
        <button
          style="margin:auto;display:block"
          class="btn"
          v-if="forms < 10 && form ===forms"
          @click="forms++"
        >Add</button>
      </div>
    </div>
    <div>Журнал запросов:</div>
    <journal :data="journal" />
  </div>
</template>

<script>
import distanceForm from "./components/distanceForm";
import journal from "./components/journal";
export default {
  name: "app",
  components: {
    distanceForm,
    journal
  },
  methods: {
    addJournalItem({ a, b, result }) {
      const date = new Date();
      this.journal.push({
        a,
        b,
        result,
        date
      });
    }
  },
  data() {
    return {
      journal: [],
      forms: 1
    };
  }
};
</script>
