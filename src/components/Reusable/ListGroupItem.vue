<template>
  <a :class="['list-group-item', { active }]">
    <slot></slot>
  </a>
</template>

<script>
export default {
  name: 'list-group-item',
  props: { active: { type: Boolean, default: false } }, 
}
</script>
