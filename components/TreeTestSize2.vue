<template>
  <div>
    TreeTestSize2
    <tree-container :tree="tree" nodeTag="tree-node-size" @updateTree="this.updateTree()"></tree-container>
  </div>
</template>

<script>
import TreeContainer from "./TreeContainer";

export default {
  props: [],
  components: {
    TreeContainer,
  },
  data: () => {
    return {
      tree: {
        val: 1,
        hideHorizontal: true,
        children: [
          {
            val: 2,
            children: [
              {
                val: 4
              },
              {
                val: 7,
                children: [
                  {
                    val: 8
                  },
                  {
                    val: 9  
                  }
                ]
              }
            ]
          },
          {
            val: 3,
            children: [
              {
                val: 5
              },
              {
                val: 6
              }
            ]
          }
        ]
      }
    };
  },
  methods: {
    updateTree: function(){
      const vm = this
      updateNode(this.tree,1)

      function updateNode(n,i){
        vm.$set(n,'height',getLevelHeight(i))
        if(n.children){
          const childrenHeight = n.children.reduce((rtn,x)=>rtn+updateNode(x,i+1),0)
          vm.$set(n,'totalHeight',Math.max(n.height,childrenHeight))
        }else{
          vm.$set(n,'totalHeight',n.height)
        } 
        return n.totalHeight
      }
    }
  },
  beforeMount: function(){
    this.updateTree() 
  }
};

/**
 * 获取不同层级的高度，最上层为1层
 */
function getLevelHeight(i){
  return 120/i
}
</script>


<style>
</style>
