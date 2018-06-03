<template>
  <section class="container">
    <tree-test/>
    <tree-test-size/>
    <tree-test-size2/>
    <tree-test-size-collapse/>    
    <tree-test-size-collapse2/>
    <div style="height: 500px;"/> 
  </section>
</template>

<script>
import TreeTest from '~/components/TreeTest.vue'
import TreeTestSize from '~/components/TreeTestSize.vue'
import TreeTestSize2 from '~/components/TreeTestSize2.vue'
import TreeTestSizeCollapse from '~/components/TreeTestSizeCollapse.vue'
import TreeTestSizeCollapse2 from '~/components/TreeTestSizeCollapse2.vue'

export default {
  components: {
    TreeTest,
    TreeTestSize,
    TreeTestSize2,
    TreeTestSizeCollapse,
    TreeTestSizeCollapse2
  }
}
</script>

<style>
</style>
