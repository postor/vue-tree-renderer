<template>
  <div>
    TreeContainerCollpase {{nodeTag}}
    <component :is="nodeTag" :node="tree" @updateTree="updateTree()" />
  </div>
</template>

<script>
export default {
  props:['tree','nodeTag'],
  data: () => {
    return {}
  },
  methods: {
    updateTree: function(){
      console.log({updateTree:'TreeContainerCollpase'})
      this.$emit('updateTree')
    },
  },
};
</script>


<style>
</style>
