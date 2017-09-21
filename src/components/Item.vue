<template>
    <li>
        <input class="check" type="checkbox"/>
        <div :class="{bold: isFolder}" @click="toggle" @dblclick="changeType"> {{model.name}}
            <span class="btn" v-if="isFolder">[{{open ? '-' : '+'}}]</span>
        </div>
        <ul class="teste" v-show="open" v-if="isFolder">
            <item class="item" v-for="model in model.children" :model="model"></item>
            <li class="add" @click="addChild">+</li>
        </ul>
    </li>
</template>

<script>
    export default {
        name: "item",
        props: ['model'],
    
        data() { 
            return {
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
                }*/                   
                this.model.children.push({
                    name: 'Teste Elara'
                })

                this.$set(this.model, "children", this.model.children)
                // this.$forceUpdate()
            }
        },
    }
</script>

<style>

.item {
    padding-left: 22px;
    cursor: pointer;
    position: relative;
    display: block;
    padding: 10px 15px;
    margin-bottom: 1px;
    background-color: white;
    border: 1px solid;
}

.bold {
    font-weight: bold;
}

.btn {
    position: absolute;
    left: 2px;
    top: 6px;
    background-color: transparent;
    color: #d8c12f;
    
    font-weight: normal;
    text-align: center;
    vertical-align: middle;    
}


/*li ::before {
    content: '>';
    border-left: 1px solid #999;
    bottom: 50px;
    height: 100%;
    top: -16px;
    width: 1px;
} */

ul {
    padding
    padding-left: 1em;
    line-height: 1.5em;
    list-style-type: dot;
}

</style>