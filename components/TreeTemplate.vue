<template>
  <div>
    TreeTemplate
    <input v-model="node.val" />
  </div>
</template>

<script>
import TreeNode from "./TreeNode";
export default {
  extends: TreeNode,
};
</script>


<style>
</style>
