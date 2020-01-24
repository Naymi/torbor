<template>
  <form @submit.prevent="$emit('submit', data)">
    <div class="distance-form">
      <div class="distance-form__input">
        <input :disabled="disabled" name="a" type="text" v-model="data.a" />
      </div>
      <div class="distance-form__input">
        <input :disabled="disabled" name="b" type="text" v-model="data.b" />
      </div>
      <button class="distance-form__go btn" :disabled="disabled">GO</button>
      <button class="distance-form__clear btn" @click.prevent="clearData">Clear</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "viewDistanceForm",
  props: { disabled: Boolean },
  methods: {
    clearData() {
      this.data = { a: "", b: "" };
    }
  },
  data() {
    return {
      data: { a: "", b: "" }
    };
  }
};
</script>


<style lang="scss" scoped>
.distance-form {
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 20px;
  width: 100%;
  &__input {
    grid-column: span 2;
    @media screen and (max-width: 768px) {
      grid-column: span 6;
    }
  }
  &__go,
  &__clear {
    grid-column: span 1;
    @media screen and (max-width: 768px) {
      grid-column: span 3;
    }
  }
}
</style>