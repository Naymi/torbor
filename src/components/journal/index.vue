<template>
  <ul class="journal">
    <journalItem v-for="(cortege, i) in data" :key="i" :data="cortege" />
  </ul>
</template>

<script>
import journalItem from "./item";
function its(type) {
  return function(v) {
    return typeof v === type;
  };
}
const itsString = its("string");
export default {
  components: {
    journalItem
  },
  props: {
    data: {
      validator(v) {
        return v.every(
          ({ a, b, result, date }) =>
            itsString(a) &&
            itsString(b) &&
            itsString(result) &&
            date instanceof Date
        );
      }
    }
  }
};
</script>

<style lang="scss" scoped></style>
