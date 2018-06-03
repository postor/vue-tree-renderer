<template>
  <div>
    TreeContainer {{nodeTag}}
    <component :is="nodeTag" :node="tree" />
  </div>
</template>

<script>
export default {
  props:['tree','nodeTag'],
  data: () => {
    return {}
  },
  methods: {
  },
};
</script>


<style>
</style>
