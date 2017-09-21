<template>
  <div id="app">
    <ul id="demo">
      <Item class="item" :model="treeData"></Item>
    </ul>
  </div>
</template>

<script>
import Item from './components/Item.vue';

export default {
	name: "app",
  components : {
    Item
  }, 

  data () {
    return {
			treeData: {
				name : 'Bebidas',
				children : [
					{name : 'Cerveja'},
					{name : 'Tequila'},
          {
            name : 'Teste A',
            children :  [
              {name : 'Filho A'},
              {name :  'Filho AA'}
            ]
          }
				]
			}
		}
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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

/* AQUI */
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
.item {
  cursor: pointer;
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>
