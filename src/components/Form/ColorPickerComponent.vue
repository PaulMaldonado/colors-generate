<template>
    <div>
      <div class="container">
        <div class="row">
          <div class="col-md-6 col-sm-12 col-lg-6 col-xl-6 col-xxl-6 mx-auto mt-4">
            <div>
              <div class="d-flex align-items-center">
                <span class="hexadeciamal">HEX</span>
                <input
                  v-model="hexColor"
                  @input="updateColor"
                  type="text"
                  class="form-control"
                  placeholder="Ingrese un color hexadecimal"
                />
                <div
                  :style="{ backgroundColor: hexColor }"
                  class="color-circle"
                ></div>
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
    }

    .color-circle {
        width: 20px;
        height: 20px;
        border-radius: 50%;
        margin-left: 5px;
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

    .hexadecimal-color {
        color: #fff5f5;
    }
    .hexadecimal-weight {
        color: #fff5f5;
    }
</style>