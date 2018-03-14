<template>
  <div class="developed">
    <div class="developed-block">
      <div class="created-by">Created by</div>
      <div class="author">
        <a :href="telegramLink" target="_blank">{{ telegram }}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'developed',
  data(){
    return {
      author: 'belozerskiy',
    }
  },
  computed: {
    telegramLink(){
      return `https://t.me/${this.author}`
    },
    telegram(){
      return `@${this.author}`
    }
  }
}
</script>

<style>
  .developed { text-align: left; color: grey; margin-top: 25px; margin-bottom: 25px; }
  .developed-block { display: inline-block; text-align: left }
  .developed > .developed-block > .created-by { font-size: 10px }
  .developed > .developed-block > .author { font-size: 14px }
</style>
