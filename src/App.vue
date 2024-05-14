<template>
  <div class="darkmode">
    <NavbarComponent />
    <HeaderComponet />
    <ColorPickerComponent />
  </div>
</template>

<script>
import NavbarComponent from './components/navbar/NavbarComponent.vue';
import HeaderComponet from './components/header/HeaderComponent.vue';
import ColorPickerComponent from './components/Form/ColorPickerComponent.vue';

export default {
  name: 'App',
  components: {
    NavbarComponent,
    HeaderComponet,
    ColorPickerComponent,
  }
}
</script>

<style>
  html,
  body {
    padding: 0;
    margin: 0;
    height: 100%;
    background-color: var(--background-color-primary);
    color: var(--text-primary-color);
  }

  :root {
    --background-color-primary: #ebebeb;
    --background-color-secondary: #fafafa;
    --accent-color: #cacaca;
    --text-primary-color: #222;
    --element-size: 4rem;
  }

  :root.dark-theme {
    --background-color-primary: #1e1e1e;
    --background-color-secondary: #2d2d30;
    --accent-color: #3f3f3f;
    --text-primary-color: #ddd;
  }

  p {
    color: var(--text-primary-color);
  }

  .darkmode {
    background-color: var(--background-color-primary);
    height: 100vh;
    width: 100vw;
  }
</style>
