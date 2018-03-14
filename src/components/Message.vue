<template>
  <b-col xs12 class="message">
    <!-- <alert> -->
      <h3><slot></slot></h3>
    <!-- </alert> -->
  </b-col>
</template>

<script>
import Alert from './Reusable/Alert';
import BCol from './Reusable/BCol';

export default {
  name: 'Message',
  components: { Alert, BCol }
}
</script>

<style>
  .message > h3 { text-align: center; color: grey}
</style>
