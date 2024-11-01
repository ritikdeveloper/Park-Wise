<template>
  <section class="dashboard">
    <input-component @car-selected="addCar"></input-component>
    <div class="output-container">
      <output-component
        v-for="car in cars"
        :key="car.numberplate"
        :brand="car.brand"
        :model="car.model"
        :numberplate="car.numberplate"
      />
    </div>
  </section>
</template>

<script>
import InputComponent from './InputComponent.vue';
import OutputComponent from './OutputComponent.vue';
import axios from 'axios';
axios.defaults.baseURL = '//localhost:8080/';


export default {
  components: {
    OutputComponent,
    InputComponent
  },
  data() {
    return {
      cars: []
    };
  },
  methods: {
    async fetchCars() {
      try {
        const response = await axios.get('/api');
        this.cars = response.data;
      } catch (error) {
        console.error('Error fetching cars:', error);
      }
    },
    async addCar(carData) {
      try {
        const response = await axios.post('/api', carData);
        this.cars.push(response.data); 
      } catch (error) {
        console.error('Error adding car:', error);
      }
    },
    addcar(car) {
      console.log(car);
      if (!this.cars.some(existingCar => existingCar.Numberplate === car.Numberplate)) {
        this.addCar(car);
      } else {
        console.log('Car with this Numberplate already exists');
      }
    }
  },
  mounted() {
    this.fetchCars();  // Fetch cars when the component is mounted
  }
};
</script>

<style scoped>
.dashboard {
  background: linear-gradient(135deg, #1e1e2f, #2a2a4e);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
}

.output-container {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
