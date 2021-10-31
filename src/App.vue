<script setup lang="ts">
import { NCard, NTabs, NTabPane } from 'naive-ui'
import ReactiveTab from './components/ReactiveTab.vue'
import CustomRefTab from './components/CustomRefTab.vue'
import ShallowTab from './components/ShallowTab.vue';
import DollarRefTab from './components/DollarRefTab.vue';

</script>
<template>
  <n-card title="Vue Reactivity" style="margin-bottom: 16px;">
    <n-tabs type="line">
      <n-tab-pane name="ref & reactive" tab="Ref & Reactive">
        <ReactiveTab />
      </n-tab-pane>
      <n-tab-pane name="shallow" tab="Shallow Ref & Reactive">
        <ShallowTab />
      </n-tab-pane>
      <n-tab-pane name="custom" tab="Custom Ref & Reactive">
        <CustomRefTab />
      </n-tab-pane>
      <n-tab-pane name="dollar" tab="$ Ref & Reactive">
        <DollarRefTab />
      </n-tab-pane>
    </n-tabs>
  </n-card>
</template>

<style>
</style>
