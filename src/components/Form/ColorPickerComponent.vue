<template>
    <div>
      <div class="container">
        <div class="row">
          <div class="col-md-6 col-sm-12 col-lg-6 col-xl-6 col-xxl-6 mx-auto mt-4">
            <div>
              <div class="d-flex align-items-center">
                <span class="hexadecimal fw-bold">HEX</span>
                <input
                  v-model="hexColor"
                  @input="updateColor"
                  type="text"
                  class="form-control"
                  placeholder="Ingrese un color hexadecimal"
                />
                <div class="color-circle-wrapper">
                  <input type="color"
                    :style="{ backgroundColor: hexColor, }"
                    class="color-circle shadow-lg rounded-full"
                    v-model="hexColor"
                    @input="updateColor"
                  />
                </div>
              </div>
              <span class="text-danger" v-show="showErrorMessage">Ingrese un color hexadecimal válido</span>
            </div>
          </div>
        </div>
      </div>
  
      <div class="container">
        <div class="row">
          <div class="col">
            <div class="d-flex flex-wrap">
              <div class="col-md-1 col-sm-2 col-lg-1 col-xl-1 col-xxl-1 mx-1" v-for="(variant, index) in colorVariants" :key="index">
                <div class="mt-4">
                  <div :style="{ backgroundColor: variant.color }" class="color-box" @click="copyHex(variant.color)">
                    <span class="hexadecimal-color fw-bold">{{ variant.color }}</span><br>
                    <span class="hexadecimal-weight fw-bold">{{ variant.weight }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import tinycolor from 'tinycolor2';
  
  export default {
    name: 'ColorPickerComponent',
  
    data() {
      return {
        hexColor: '',
        showColorPicker: false,
        isDarkMode: false
      };
    },
  
    computed: {
     colorVariants() {
        const variants = [];
            if (this.hexColor && this.isValidHex) {
                const baseColor = tinycolor(this.hexColor);
                for (let i = 0; i < 11; i++) {
                const newColor = baseColor.clone().brighten(i * 5).toString();
                variants.push({ color: newColor, weight: i * 5 });
                }
            }
        return variants;
     },

      isValidHex() {
        return /^#([0-9A-F]{3}){1,2}$/i.test(this.hexColor);
      },

      showErrorMessage() {
        return this.hexColor && !this.isValidHex;
      }
    },
  
    methods: {
      updateColor() {
  
      },

      openColorPicker() { 
        this.showColorPicker = true;
      },

      toggleColorPicker() {
        this.showColorPicker = !this.showColorPicker;
      },

      onColorChange(color) {
        if (color && color) {
          this.hexColor = color.hex;
          this.showColorPicker = false;
        }
      },

      doCopy: function () {
        this.$copyText(this.message).then(function (e) {
          alert('Copied')
          console.log(e)
        }, function (e) {
          alert('Can not copy')
          console.log(e)
        })
      },
  
      copyHex(hex) {
        navigator.clipboard.writeText(hex).then(() => {
          alert('¡El color hexadecimal se copió al portapapeles!');
        }, (err) => {
          console.error('Error al copiar el color hexadecimal: ', err);
        });
      }
    }
  }
  </script>

<style scoped>
    .color-box {
        width: 90px;
        height: 90px;
        margin-right: 5px;
        display: inline-block;
        cursor: pointer;
        border-top-left-radius: 8px;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
        border-bottom-left-radius: 8px;
        box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        text-align: center;
        padding-top: 15px;
        padding: 10px;
        text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.5);
    }

    .color-circle {
        box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.5);
        color: black;
        cursor: pointer;
        width: 100%;
        height: 100%;
        border: none;
        padding: 0;
    }

    .color-circle-wrapper {
      margin-left: 5px;
      width: 45px;
      height: 40px;
      border-radius: 50%;
      overflow: hidden;
    }

    .form-control {
        padding: .700rem .75rem;
        border-top-left-radius: 20px;
        border-top-right-radius: 20px;
        border-bottom-right-radius: 20px;
        border-bottom-left-radius: 20px;
        border-color: #ced4da;
        box-shadow: none;
    }

    .color-circle-dark-mode {
      background-color: white;
      color: black;
    }

    .hexadecimal-color {
        color: white;
        font-weight: bold;
        opacity: 0.8;
    }
    .hexadecimal-weight {
        color: white;
        font-weight: bold;
        opacity: 0.8;
    }

    :root.dark-theme {
      --background-color-primary: #1e1e1e;
      --background-color-secondary: #2d2d30;
      --accent-color: #3f3f3f;
      --text-primary-color: #ddd;
      --background-form-control-primary: #ddd;
      --text-hexa-dark-mode-primary: white;
    }

    .hexadecimal {
      color: var(--text-primary-color);
      margin-right: 10px;
    }
</style>