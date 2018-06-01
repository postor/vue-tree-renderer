<template>
  <div class="level">
    <div class="horizontal"></div>
    <div class="node-title">
      <span>{{node.val}}</span>
    </div>
    <div class="box" v-if="node.children&&node.children.length">
      <div class="horizontal-parent"></div>
      <div class="virtical"></div>
      <tree-node :node="n" @updateNode="updateNode(i,$event)" v-for="(n,i) in node.children||[]" :key="i"></tree-node>  
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
    }
  }
};
</script>

<style>
</style>
