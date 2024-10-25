<template>
  <section class="dashboard">
    <input-component @car-selected="addcar"></input-component>
    <div class="output-container">
      <OutputComponent
        v-for="car in cars"
        :key="car.Numberplate"
        :Brand="car.Brand"
        :Model="car.Model"
        :Color="car.Color" 
        :Numberplate="car.Numberplate"
        :Towerno="car.Towerno"
        :Flatno="car.Flatno"
      />
    </div>
  </section>
</template>

<script>
import InputComponent from './InputComponent.vue';
import OutputComponent from './OutputComponent.vue';

export default {
  components: {
    OutputComponent,
    InputComponent
  },
  data() {
    return {
      cars: [
        {
          Brand: 'Maruti',
          Model: 'Baleno',
          Color: 'Orange',
          Numberplate: 'HR36ABxxxx',
          Towerno: 'M-7',
          Flatno: 628
        },
        {
          Brand: 'Hyundai',
          Model: 'Creta',
          Color: 'White',
          Numberplate: 'HR26ADxxxx',
          Towerno: 'M-9',
          Flatno: 986
        }
      ]
    };
  },

  methods:{
    addcar(car){
        console.log(car);
        this.cars.push(car);
    }
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
