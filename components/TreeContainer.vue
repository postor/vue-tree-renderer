<template>
  <div>
    TreeContainer {{nodeTag}}
    <component :is="nodeTag" :node="tree" @updateNode="updateTree($event)" />
  </div>
</template>

<script>
export default {
  props:['tree','nodeTag'],
  data: () => {
    return {}
  },
  methods: {
    updateTree: function(tree){
      this.$emit('updateTree',tree)
    }
  },
};
</script>


<style>
</style>
