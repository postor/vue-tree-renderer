<template>
  <div>
    TreeTestSizeCollapse
    <tree-container :tree.sync="tree" nodeTag="tree-node-size-collapse" @updateTree="updateTree()"></tree-container>
  </div>
</template>

<script>
import TreeContainer from "./TreeContainerCollpase";

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
      console.log(`update tree`)
      const vm = this
      updateNode(this.tree,1)

      function updateNode(n,i){
        vm.$set(n,'height',getLevelHeight(i))
        if(n.children && !n.collpase){
          const childrenHeight = n.children.reduce((rtn,x)=> rtn + updateNode(x,i+1),0)
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
  return 40
}
</script>


<style>
</style>
