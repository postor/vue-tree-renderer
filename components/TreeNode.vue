<template>
  <div class="node-level">
    <div class="node-horizontal" :style="horizontalStyle" v-if="!node.hideHorizontal"></div>
    <div class="node-title">
      <span>{{node.val}}</span>
    </div>
    <div class="node-box" v-if="node.children&&node.children.length">
      <div class="node-horizontal-parent" :style="horizontalParentStyle"></div>
      <div class="node-virtical-parent" :style="virticalParentStyle" v-if="node.children&&node.children.length>1"></div>
      <tree-node 
        :node="n" 
        v-for="(n,i) in node.children||[]" 
        :key="i"
      ></tree-node>  
    </div>  
  </div>
  
</template>

<script>
export default {
  props: ["node"],
  methods: {
    getTotalHeight(node){
      return getHeight(node)
      
      function getHeight(node){
        if(!node.children || node.children.length == 0){
          return 40
        }
        return node.children.reduce((rtn, n) => rtn += getHeight(n), 0)
      }  
    }
  },
  computed:{
    horizontalStyle: function(){
      return {
        borderTop: '1px solid green',
      }
    },    
    horizontalParentStyle: function(){      
      return {
        borderTop: '1px solid green',
      }
    },
    virticalParentStyle: function(){

      const height = (this.node.children && this.node.children.length>1)
        ?this.node.children.slice(0,this.node.children.length-1).reduce((rtn,n)=>rtn+this.getTotalHeight(n),0)
        :0

      return {
        borderLeft: `1px solid green` ,
        width: `0`,
        left: `-50px`,
        top: `20px`,
        height: `${height}px`, 
      }
    },
  }
};
</script>

<style>
</style>
