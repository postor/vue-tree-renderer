<template>
  <div class="node-level">
    <div class="node-horizontal" v-if="!node.hideHorizontal"></div>
    <div class="node-title">
      <span>{{node.val}}</span>
    </div>
    <div class="node-box" v-if="node.children&&node.children.length">
      <div class="node-horizontal-parent" ></div>
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
    virticalParentStyle: function(){
      const height = (this.node.children && this.node.children.length>1)
        ?this.node.children.slice(0,this.node.children.length-1).reduce((rtn,n)=>rtn+this.getTotalHeight(n),0)
        :0
        
      return {
        border: '0 none',
        borderLeft: `1px solid green` ,
        width: `0`,
        top: `20px`,
        height: `${height}px`, 
      }
    },
  }
};
</script>

<style>
</style>
