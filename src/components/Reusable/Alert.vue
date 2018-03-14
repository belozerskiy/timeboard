<template>
  <div :class="['alert', `alert-info`]">
    <strong><slot></slot></strong>
  </div>
</template>

<script>
export default {
  name: 'message',
}
</script>

