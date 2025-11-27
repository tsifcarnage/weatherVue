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
  <form class="flex gap-2 justify-center" @submit.prevent="submit">
    <input
      v-model="city"
      minlength="3"
      class="text-red-500 border-amber-700 border-2 p-2 rounded-2xl w-full"
      type="text"
      placeholder="Chercher une ville"
    />
    <button type="submit"><i class="fa-solid fa-magnifying-glass"></i></button>
  </form>
</template>
<style scoped>
button {
  border: 2px solid rgb(167, 80, 48);
  transition: all 0.2s ease;
}
button:hover {
  background-color: rgb(167, 80, 48);
}
</style>
