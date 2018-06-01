<template>
  <div>
    TreeTest
    <tree-container :tree="tree" nodeTag="tree-node" @updateTree="this.tree=$event"></tree-container>
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
        children: [
          {
            val: 2,
            children: [
              {
                val: 4
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
