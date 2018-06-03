<template>
  <div>
    TreeTest
    <tree-container :tree="tree" nodeTag="tree-node-basic" ></tree-container>
    <tree-container :tree="tree" nodeTag="tree-node-css" ></tree-container>
    <tree-container :tree="tree" nodeTag="tree-node" ></tree-container>
    <tree-container :tree="tree" nodeTag="tree-node-center" ></tree-container>
  </div>
</template>

<script>
import TreeContainer from "./TreeContainer";

export default {
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
  }
};
</script>


<style>
</style>
