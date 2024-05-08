<template>
  <div>
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
    ColorPickerComponent
  }
}
</script>
