<template>
    <li class="teste">
        <!--{{model.isEnabled}}-->
        <input type="checkbox" :value="model.name" v-model="model.isEnabled" @click="checkAll"></input>
        <div :class="{bold: isFolder}" @click="toggle" @dblclick="changeType"> {{model.name}}
            <span class="btn" v-if="isFolder">[{{open ? '-' : '+'}}]</span>
        </div>
        <ul v-show="open" v-if="isFolder">
            <item class="item" v-for="model in model.children" :model="model"></item>   
        </ul>
    </li>
</template>

<script>
    export default {
        name: "item",
        props: ['model'],
    
        data() { 
            return {
                //isEnabled: false,
                open: false
            }
        },

        computed: {
            isFolder: function() {    
                return this.model.children && this.model.children.length
            }
        },

        methods: {
            toggle: function (){
                if(this.isFolder){
                    this.open = !this.open
                }
            },

            changeType: function(){
                if (!this.isFolder) {
                    this.$set(this.model, 'children', [])
                    this.addChild()
                    this.open = true
                }
            },

            addChild: function() {
                /*console.log(this.$set, this.model, "teste");
                if (!this.model.children) {
                    this.model.children = []
                }   */              
                this.model.children.push({
                    name: 'Teste Elara'
                })

                this.$set(this.model, "children", this.model.children)
                // this.$forceUpdate()
            },

            checkAll: function () {
                let checked = this.model.isEnabled;
                let teste = (current, checked) => {
                debugger;
                    this.$set(current, 'isEnabled', checked);
                    if (current.children) {
                        current.children.forEach(children => {
                            teste(children, checked);
                        });
                    }
                }
                teste(this.model, checked);
            }
        }
    }
</script>

<style>

li input {
    position: absolute;
    left: 0;
    margin-left: 0;
    height: 1em;
    width: 1em;
}

.teste {
    width: 300px;
    padding-left: 30px;
    position: relative;
    display: block;
    padding: 10px 15px;
    margin-bottom: 1px;
    background-color: white;
}

.btn {
    position: inherit;
    left: 2px;
    top: 6px;
    background-color: transparent;
    color: #d8c12f;
    text-align: center;
    vertical-align: middle;    
}
</style>