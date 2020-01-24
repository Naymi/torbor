<template>
  <li>
    {{ date }} в {{ time }} {{ data.a }} - {{ data.b }} =
    <span v-html="data.result" />
  </li>
</template>

<script>
function formatTwoSymvolNumber(number) {
  return String(number).padStart(2, "0");
}
export default {
  computed: {
    date() {
      return (
        formatTwoSymvolNumber(this.data.date.getMonth() + 1) +
        "/" +
        formatTwoSymvolNumber(this.data.date.getDate())
      );
    },
    time() {
      return (
        formatTwoSymvolNumber(this.data.date.getHours()) +
        ":" +
        formatTwoSymvolNumber(this.data.date.getMinutes())
      );
    }
  },
  props: {
    data: {
      a: { required: true, type: Number },
      b: { required: true, type: Number },
      result: { required: true, type: String },
      date: {
        required: true,
        type: Date
      }
    }
  }
};
</script>