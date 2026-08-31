<script setup>
  import { ref } from 'vue';
  import { getColorSync, getPaletteSync } from 'colorthief';

  const url = ref('');
  const dominantColor = ref('');
  const colorPalette = ref([]);

  function extractColors(event) {
    try { 
      const img = event.target;
      const color = getColorSync(img);

      dominantColor.value = color.hex();
      colorPalette.value = getPaletteSync(img, { colorCount: 5 });
    } catch(err) {
      console.error(`Unable to download image: ${err.message}`);
    }
  }
</script>

<template>
    <div class="imageContainer">
      <img :src="url" class="userImage" crossorigin="anonymous" @load="extractColors($event)">
    </div>
    <br />
    <div class="userInput">
      <label>Image Url</label>
      <input v-model="url" placeholder="Image URL.." />
    </div>


    <div class="dominantContainer">
      <p>Dominant color</p>
      <div class="swatch" :style="{ backgroundColor: dominantColor }"></div>
    </div>
    <div class="paletteContainer">
      <div 
        v-for="(color, index) in colorPalette" 
        :key="index" 
        class="swatch" 
        :style="{ backgroundColor: color.css() }">
      </div>
    </div>
</template>

<style scoped>

.userInput {
  display: flex;
  justify-content: center;
}

.imageContainer{
  display: flex;
  justify-content: center;
}

.userImage {
  width: 50%;
  max-width: 400px;
  height: auto;
  object-fit: cover;
}

.dominantContainer {
  display: flex;
  justify-content: center;
  margin: 20px;
}

.paletteContainer {
  display: flex;
  margin: 20px;
  justify-content: center;

}

.swatch {
  width: 40px;
  height: 40px;
  margin: 5px;
}

</style>
