<template>
  <div class="two-side-block">
    <div class="pull-left">
      <slot name="left"></slot>
    </div>
    <div class="pull-right">
      <slot name="right"></slot>
    </div>
    <div class="clearfix"></div>    
  </div>
</template>

<script>
export default {
  name: 'two-side-block',
}
</script>
<style>
  .two-side-block { margin-bottom: 25px; }
</style>
