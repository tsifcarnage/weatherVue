<script>
export default {
  data() {
    return {
      city: "",
    };
  },
  methods: {
    submit() {
      this.$emit("search", this.city.trim());
    },
  },
};
</script>
<template>
  <form @submit.prevent="submit">
    <input
      v-model="city"
      minlength="3"
      class="text-red-500 border-amber-700 border-2 p-2 rounded-2xl"
      type="text"
      placeholder="Chercher une ville"
    />
    <button class="p-2 mx-2 bg-teal-400" type="submit">🔍</button>
  </form>
</template>
<style scoped></style>
