<template>
  <ul class="output-list">
    <li>Car brand is {{ brand }}</li>
    <li>Car model is {{ model }}</li>
    <!-- <li>Car color is {{ Color }}</li> -->
    <li>Car numberplate is {{ numberplate }}</li>
    <!-- <li>Owner's address is {{ Towerno }} {{ Flatno }}</li> -->
  </ul>
</template>

<script>
export default {
  props: ['brand', 'model',  'numberplate'],
};
</script>

<style scoped>
.output-list {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  padding: 15px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  margin: 5px 0;
  color: #ffffff;
}

.output-list li {
  margin: 5px 0;
}
</style>
