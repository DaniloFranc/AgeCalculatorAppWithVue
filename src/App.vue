<template>
  <div id="app">
    <AgeCalculator />
  </div>
</template>

<script>
import AgeCalculator from './components/AgeCalculator.vue'

export default {
  name: 'App',
  components: {
    AgeCalculator
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

@font-face {
 font-family: 'Poppins';
 src: url(../src/assets/fonts/Poppins-Regular.ttf) format('truetype');
 font-weight: 400;
 font-style: normal;
}   
    
@font-face {
 font-family: 'Poppins-Bold';
 src: url(../src/assets/fonts/Poppins-Bold.ttf) format('truetype');
 font-weight: 200;
 font-style: normal;
} 
@font-face {
 font-family: 'Poppins-Italic';
 src: url(../src/assets/fonts/Poppins-Italic.ttf) format('truetype');
 font-weight: 700;
 font-style: normal;

} 

@font-face {
  font-family: 'Poppins-ExtraBoldItalic';
  src: url(../src/assets/fonts/Poppins-ExtraBoldItalic.ttf) format('truetype');
  font-weight: 700;
  font-style: italic;
}
        

@font-face {

  font-family: 'Poppins-ExtraBold';
  src: url(../src/assets/fonts/Poppins-ExtraBold.ttf) format('truetype');
  font-weight: 700;
  font-style: normal;

}



body {
  font-family: 'Poppins', sans-serif;
  background-color: #f2f2f2;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
