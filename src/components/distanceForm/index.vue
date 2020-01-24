<template>
  <div>
    <distanceFormView v-if="ymapsReady" @submit="calculate" :disabled="disabled" />
    <preloader v-else />
  </div>
</template>

<script>
import distanceFormView from "./view";
import preloader from "../preloader";
export default {
  created() {
    window.ymaps.ready(() => (this.ymapsReady = true));
  },
  name: "smartDistanceForm",
  components: {
    distanceFormView,
    preloader
  },
  data() {
    return {
      ymapsReady: false,
      disabled: false
    };
  },
  methods: {
    calculate(data) {
      this.disabled = true;
      const { a, b } = data;
      window.ymaps.route([a, b]).done(
        r => {
          this.disabled = false;
          this.$emit("calculate", { a, b, result: r.getHumanLength() });
        },
        err => {
          this.disabled = false;
          this.$emit("calculate", {
            a,
            b,
            result: "Fetch Error - " + JSON.stringify(err)
          });
        }
      );
    }
  }
};
</script>
