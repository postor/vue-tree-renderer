<template>
  <div>
    <span>{{node.val}}</span>
    <tree-node-basic 
      :node="n" 
      v-for="(n,i) in node.children||[]" 
      :key="i"
    ></tree-node-basic>  
  </div>
</template>

<script>
export default {
  props: ["node"],
};
</script>

<style>
</style>
