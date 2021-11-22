<template>
<div class="container">
  <header v-bind:style="styleObject">
    <slot name="header" :title='title'></slot>
  </header>
  <main v-for="x in names" :key="x.nome" v-bind:style="x.styleObject">
      <div>
        <slot name="main" :nome="x.nome" :sobrenome="x.sobrenome"></slot>
      </div>
  </main>
  <footer  v-for="x in names" :key="x.nome"  >
    <slot name="footer" :nome="x.nome" :sobrenome="x.sobrenome"  ></slot>
  </footer>
</div>
</template>

<script>
export default {
  name: 'ExercicioUm',
  data(){
      return {
        title: 'Lista de nomes',
        styleObject: {
            color: 'red',
            fontSize: '13px'
        },
        names : [
              {nome: 'Monteiro', sobrenome: 'Lobato',  
               styleObject: {
                    color: 'blue',
                    fontSize: '30px'
              }},
              {nome: 'José' , sobrenome: 'de Alencar',  
                styleObject: {
                    color: 'blue',
                    fontSize: '30px'
              }},
              {nome: 'Cecília', sobrenome: 'Meireles',  
                styleObject: {
                    color: 'red',
                    fontSize: '20px'
              }},
              {nome: 'Clarice', sobrenome: 'Lispector',  
                styleObject: {
                    color: 'red',
                    fontSize: '20px'
              }},
              {nome: 'Mario', sobrenome: 'Quintana',  
                styleObject: {
                    color: 'blue',
                    fontSize: '30px'
              }}
        ]
    }
  },
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>