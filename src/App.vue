<template>
  <div id="app">
    <ul id="demo">
      <Item class="item" :model="treeData"></Item>
    </ul>
    <!--<button v-on:click="checkAll">Selecionar</button>-->
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
				name : 'Filmes',
				children : [
					{name : 'Ação'},
					{name : 'Terror'},
          {
            name : 'Suspense',
            children :  [
              {name : 'Suspense A'},
              {name :  'Suspense B'}
            ]
          }
				]
			}
		}
  }
}
</script>

<style>

body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
  width: 500px;
  border: 1px solid;
}

.bold {
  font-weight: bold;
  text-align: left;
}


ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>
