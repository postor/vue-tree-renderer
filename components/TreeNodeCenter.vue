<template>
  <div class="node-level">
    <div class="node-horizontal" :style="horizontalStyle" v-if="!node.hideHorizontal"></div>
    <div class="node-title" style="align-self: center;">
      <span>{{node.val}}</span>
    </div>
    <div class="node-box" v-if="node.children&&node.children.length">
      <div class="node-horizontal-parent" :style="horizontalParentStyle"></div>
      <div class="node-virtical-parent" :style="virticalParentStyle" v-if="node.children&&node.children.length>1"></div>
      <tree-node-center 
        :node="n" 
        @updateNode="updateNode(i,$event)"         
        @updateCenter="updateCenter(i,$event)" 
        v-for="(n,i) in node.children||[]" 
        :key="i"
      ></tree-node-center>  
    </div>  
  </div>
  
</template>

<script>
export default {
  props: ["node"],
  methods: {
    updateNode: function(i, nodeData) {
      const oldChildren = this.node.children;
      this.$emit(
        "updateNode",
        Object.assign({}, this.node, {
          children: oldChildren
            .slice(0, i)
            .concat([nodeData])
            .concat(oldChildren.slice(0, i + 1))
        })
      );
    },
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
      const top = this.getTotalHeight(this.node)/2    
      return {
        borderTop: '1px solid green',
        width: `50px`,
        left: `-50`,
        top: `${top}px`
      }
    },    
    horizontalParentStyle: function(){  
      const top = this.getTotalHeight(this.node)/2    
      return {
        borderTop: '1px solid green',
        width: `50px`,
        left: `-100px`,
        top: `${top}px`
      }
    },
    virticalParentStyle: function(){
      const offset = this.getTotalHeight(this.node.children[0])/2
      const height = 
        offset 
        + this.node.children
          .slice(1,this.node.children.length-1)
          .reduce((rtn,node)=>rtn+this.getTotalHeight(node),0)
        + this.getTotalHeight(this.node.children[this.node.children.length-1])/2
      
      return {
        borderLeft: `1px solid green` ,
        width: `0`,
        left: `-50px`,
        top: `${offset}px`,
        height: `${height}px`, 
      }
    },
  }
};
</script>

<style>
</style>
