<template>
  <div class="node-level">
    <div class="node-horizontal" :style="horizontalStyle" v-if="!node.hideHorizontal"></div>
    <div class="node-title" :style="titleStyle">
      <span>{{node.val}}</span>
    </div>
    <div class="node-box" v-if="node.children&&node.children.length">
      <div class="node-horizontal-parent" :style="horizontalParentStyle"></div>
      <div class="node-virtical-parent" :style="virticalParentStyle" v-if="node.children&&node.children.length>1"></div>
      <tree-node-size 
        :node="n" 
        v-for="(n,i) in node.children||[]" 
        :key="i"
      ></tree-node-size>  
    </div>  
  </div>
  
</template>

<script>
export default {
  props: ["node"],
  methods: {
    getTotalHeight(node){
      return node.totalHeight
    }
  },
  computed:{
    titleStyle: function(){
      return {
        boxSizing: `border-box`,
        border: `1px solid red`,
        lineHeight: `${this.node.height}px`,        
        height: `${this.node.height}px`,
      }
    },
    horizontalStyle: function(){
      return {
        borderTop: '1px solid green',
        top: `${this.node.height/2}px`,
      }
    },    
    horizontalParentStyle: function(){      
      return {
        borderTop: '1px solid green',
        top: `${this.node.height/2}px`,
      }
    },
    virticalParentStyle: function(){
      let height = 0, offset = 0
      if(this.node.children && this.node.children.length){
        //假设下层的高度总是更小的
        offset = this.node.children[0].height/2
        if(this.node.children.length == 1){
          height = this.node.height/2 - offset
        }else{
          height = this.node.children
            .slice(0,this.node.children.length-1)
            .reduce((rtn,x)=>rtn+x.totalHeight,0)
            - offset + this.node.children[this.node.children.length-1].height/2
        }
      }

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
