<template>
  <div>
    <h1>Escolha uma cor</h1>
      <input type="color" @change="paletaDeCor($event)">
  </div>
  <ExercicioUm>
    <template v-slot:header="slotA">
      <h1>{{slotA.title}}</h1>
    </template>

    <template v-slot:main="slotA">
      <div>{{slotA.nome}} {{slotA.sobrenome}}</div>
    </template>

    <template v-slot:footer="slotA">
       <div>{{slotA.nome}} {{slotA.sobrenome}}</div>
    </template>
  </ExercicioUm>

  <div id="app">
    <h2>Barra de Cores</h2>
    <Canvas style="width: 100%; height: 600px;">
      <Caixa
        v-for="(obj, index) of chartValues"
        :key=index
        :x1="(index / chartValues.length) * 100"
        :x2="(index / chartValues.length) * 100 + 100 / chartValues.length"
        :y1="100"
        :y2="100 - obj.val"
        :color="obj.color"
        :value="obj.val"
      >
      </Caixa>
    </Canvas>
  </div>
  
</template>

<script>
import ExercicioUm from './components/ExercicioUm.vue'
import Canvas from './components/Canvas.vue'
import Caixa from './components/Caixa.vue'

export default {
  name: 'App',
  components: {
    ExercicioUm,
    Caixa,
    Canvas
  },
   data() {
    return {
      chartValues: [
        { val: 24, color: 'red' },
        { val: 32, color: '#0f0' },
        { val: 66, color: 'rebeccapurple' },
        { val: 1, color: 'green' },
        { val: 28, color: 'blue' },
        { val: 60, color: 'rgba(150, 100, 0, 0.2)' },
      ],
    };
  },
  methods: {
  paletaDeCor(e){
    console.log(e.target.value)
    }
  },
  mounted() {
    let dir = 1;
    let selectedVal = Math.floor(Math.random() * this.chartValues.length);

    setInterval(() => {
      if (Math.random() > 0.995) dir *= -1;
      if (Math.random() > 0.99)
        selectedVal = Math.floor(Math.random() * this.chartValues.length);

      this.chartValues[selectedVal].val = Math.min(
        Math.max(this.chartValues[selectedVal].val + dir * 0.5, 0),
        100
      );
    }, 16);
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
