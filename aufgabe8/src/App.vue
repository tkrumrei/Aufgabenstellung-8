 <template>
  <div class="bg-gray-600 text-white w-1/2 m-auto mt-12">
    <div class="text-center border-b-2 border-black py-4">
        <h1 class="text-3xl"> Entfernung zum Geo1 Gebäude</h1>
    </div>
    <div v-for="(i, index) in aufgabe8" :key="i.name">
      <Aufgabe8Item 
        :a8name="i.name" 
        :a8Index="index"
        :a8Entfernung=calculateDistance(index)
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

      poi: {name: "Geo1", cor: [7.595737,51.969508]},
      aufgabe8: [
        {name: "Köln", cor: [6.9570, 50.9367], entfernung: 0},
        {name: "Amsterdam", cor: [4.9041, 52.3676], entfernung: 0},
        {name: "Kassel", cor: [9.4797, 51.3127], entfernung: 0},
        {name: "Barcelona", cor: [2.1686, 41.3874], entfernung: 0},
        {name: "Tunis", cor: [10.1815, 36.8065], entfernung: 0},
        {name: "Kyoto", cor: [135.7681,35.0116], entfernung: 0},
        {name: "Bucharest", cor: [26.1025, 44.4268], entfernung: 0},
        {name: "Graz", cor: [15.4395, 47.0707], entfernung: 0},
        {name: "Kairo", cor: [31.2357, 30.0444], entfernung: 0},
        {name: "Dublin", cor: [6.2603, 53.3498], entfernung: 0},
        {name: "Oslo", cor: [10.7522, 59.9139], entfernung: 0},
      ],
    };
  },
  methods: {
    deletePOI(index) {
      this.aufgabe8.splice(index, 1)
    },
    calculateDistance(i) {
      var lat1 = this.poi.cor[1];
      var lon1 = this.poi.cor[0];
      // Punkte von cities-Array als zweiten Punkt speichern 
      var lat2 = this.aufgabe8[i].cor[1];
      var lon2 = this.aufgabe8[i].cor[0];
      
      const R = 6371e3; // metres
      const φ1 = lat1 * Math.PI/180; // φ, λ in radians
      const φ2 = lat2 * Math.PI/180;
      const Δφ = (lat2-lat1) * Math.PI/180;
      const Δλ = (lon2-lon1) * Math.PI/180;

      const a = Math.sin(Δφ/2) * Math.sin(Δφ/2) +
            Math.cos(φ1) * Math.cos(φ2) *
            Math.sin(Δλ/2) * Math.sin(Δλ/2);
      const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));

      var d = Math.round((R * c / 1000) * 10) / 10; // in km umgerechnet und auf eine Nachkommastelle gerundet

      return d;
    }
  },
  components: {
    Aufgabe8Item,
  }
}
</script>

