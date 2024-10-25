<template>
  <form @submit.prevent="validate" class="input-form">
    <label>Car Company</label>
    <input placeholder="Enter Company Name" v-model="Brand" />
    
    <label>Car Model</label>
    <input placeholder="Enter Car Model" v-model="Model" />
    
    <label>Car Color</label>
    <input placeholder="Enter Car Color" v-model="Color" />
    
    <label>Car's Numberplate</label>
    <input placeholder="Enter Numberplate" v-model="Numberplate" />
    
    <label>Owner's Tower No</label>
    <input placeholder="Enter Tower No" v-model="Towerno" />
    
    <label>Owner's Flat No</label>
    <input placeholder="Enter Flat No" v-model="Flatno" />
    
    <div class="button-container">
      <button type="submit">Save Data</button>
      <p v-if="!validates" class="error-message">Please enter all data</p>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      Brand: null,
      Model: null,
      Color: null,
      Numberplate: null,
      Towerno: null,
      Flatno: null,
      validates: true,
    };
  },
  methods: {
    submitForm() {
      this.$emit('car-selected', {
        Brand: this.Brand,
        Model: this.Model,
        Color: this.Color,
        Numberplate: this.Numberplate,
        Towerno: this.Towerno,
        Flatno: this.Flatno,
      });
    },
    validate() {
      if (
        !this.Brand ||
        !this.Model ||
        !this.Color ||
        !this.Numberplate ||
        !this.Towerno ||
        !this.Flatno
      ) {
        this.validates = false;
      } else {
        this.validates = true; 
        this.submitForm(); 
      }
    },
  },
};
</script>

<style scoped>
.input-form {
  background: linear-gradient(135deg, #3a3a5a, #5a5a8a);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.input-form label {
  color: #ffffff;
  font-weight: bold;
  display: block;
  margin: 10px 0 5px;
}

.input-form input {
  width: calc(100% - 20px);
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  border-radius: 5px;
  background: #e0e0e0;
}

.button-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.button-container button {
  background: #5cb85c;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  cursor: pointer;
}

.error-message {
  color: #d9534f;
}
</style>
