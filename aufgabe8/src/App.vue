 <template>
  <div class="bg-gray-600 text-white w-1/2 m-auto mt-12">
    <div class="text-center border-b-2 border-black py-4">
      <h1 class="text-3xl"> Unsere POIS</h1>
    </div>
    <div v-for="(i, index) in aufgabe8" :key="i.name">
      <Aufgabe8Item 
        :a8name="i.name" 
        :a8Index="index"
        :a8Entfernung="i.entfernung"
        @removePOI-index="deletePOI"/>
    </div>
  </div>
</template>

<script>
import Aufgabe8Item from "./components/Aufgabe8Item.vue";

export default {
  name: 'App',
  data() {
    return {

      poi: {name: "Geo1", done: [7.595737,51.969508]},
      aufgabe8: [
        {name: "Köln", done: [6.9570, 50.9367], entfernung: 0},
        {name: "Amsterdam", done: [4.9041, 52.3676], entfernung: 0},
        {name: "Kassel", done: [9.4797, 51.3127], entfernung: 0},
        {name: "Barcelona", done: [2.1686, 41.3874], entfernung: 0},
        {name: "Tunis", done: [10.1815, 36.8065], entfernung: 0},
        {name: "Kyoto", done: [135.7681,35.0116], entfernung: 0},
        {name: "Bucharest", done: [26.1025, 44.4268], entfernung: 0},
        {name: "Graz", done: [15.4395, 47.0707], entfernung: 0},
        {name: "Kairo", done: [31.2357, 30.0444], entfernung: 0},
        {name: "Dublin", done: [6.2603, 53.3498], entfernung: 0},
        {name: "Oslo", done: [10.7522, 59.9139], entfernung: 0},
      ],
      
    };
  },
  methods: {
    deletePOI(index) {
      this.aufgabe8.splice(index, 1)
    }
  },
  components: {
    Aufgabe8Item,
  }
}
</script>

