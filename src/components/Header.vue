<template>
  <header class="logo">
    <h1 class="logo-heading"><span class="logo-number">7</span>wonders</h1>
  </header>
</template>

<script>

export default {
  name: 'Header',
}
</script>

<style>

.logo-heading {
  width: 100%;
  position: relative;
  text-transform: uppercase;
  font-size: 25px;
  line-height: 1.4;
}

.logo-number {
  display: block;
  position: absolute;
  top: -10px;
  left: -20px;
  font-size: 38px;
  line-height: 1.4;
  font-weight: 500;
}

</style>
