<template>
  <div class="flex justify-between items-center py-4 px-4">
    <h1>{{ name }}</h1>
    <p class="px-3"> {{ entfernung }} km</p>
    <button class="bg-red-600 py-1 px-1 rounded" @click="removePOI">Delete Point</button>
  </div>
</template>

<script>
export default {
  name: "Aufgabe8Item",
  props:["a8name", "a8Index", "a8Entfernung"],
  data() {
    return{
      name: this.a8name,
      entfernung: this.a8Entfernung,
    }
  },
  methods: {
    removePOI() {
      this.$emit("removePOI-index", this.a8Index)
    }
  },
}
</script>
