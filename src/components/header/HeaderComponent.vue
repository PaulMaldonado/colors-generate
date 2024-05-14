<template>
  <div class="mt-4">
    <h1 class="text-center fw-bold mt-4 title-header">CSS COLORS <br>GENERATOR</h1>
    <p class="text-center mt-4 subtitle-header">Press input, enter a Hexadecimal code <br>to generate color palette.</p>
  </div>
</template>

<script>
export default {
    name: 'HeaderComponent'
}
</script>

<style scoped>
    .title-header {
        font-size: 50px;
        color: #3e3b3b;
    }

    .subtitle-header {
        font-size: 20px;
        color: #474343;
        font-weight: 400;
    }

    :root.dark-theme {
      --background-color-primary: #1e1e1e;
      --background-color-secondary: #2d2d30;
      --accent-color: #3f3f3f;
      --text-primary-color: #ddd;
    }

    .title-header {
      color: var(--text-primary-color)
    }

    .subtitle-header {
      color: var(--text-primary-color);
    }
</style>