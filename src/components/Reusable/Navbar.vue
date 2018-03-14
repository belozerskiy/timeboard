<template>
  <div class="navbar navbar-default navbar-inverse">
    <div class="container-fluid">
      <div class="navbar-header">
        <a class="navbar-brand" href="#">
          <strong>{{ title }}</strong>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'navbar',
  props: { title: { type: String, required: true } }
}
</script>
