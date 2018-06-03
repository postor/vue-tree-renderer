<template>
  <div class="node-level">
    <div class="node-horizontal" v-if="!node.hideHorizontal"></div>
    <div class="node-title">
      <span>{{node.val}}</span>
    </div>
    <div class="node-box" v-if="node.children&&node.children.length">
      <div class="node-horizontal-parent"></div>
      <div class="node-virtical-parent" v-if="node.children&&node.children.length>1"></div>
      <tree-node-css 
        :node="n" 
        v-for="(n,i) in node.children||[]" 
        :key="i"
      ></tree-node-css>  
    </div>  
  </div>
  
</template>

<script>
export default {
  props: ["node"],
};
</script>

<style>
</style>
