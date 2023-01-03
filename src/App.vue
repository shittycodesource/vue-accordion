<template>
  <div id="app">
    <svg display="none" fill="none" xmlns="http://www.w3.org/2000/svg">
      <symbol id="down" viewBox="0 0 24 15">
        <path d="M2.83 0.0849915L12 9.25499L21.17 0.0849915L24 2.91499L12 14.915L0 2.91499L2.83 0.0849915Z"/>
      </symbol>
    </svg>

    <div class="wrapper">
      <Accordion
        :title="accordionTitle"
        :text="accordionText"
      />
      <Accordion
        :title="accordionTitle"
        :text="accordionText"
      />
      <Accordion
        :title="accordionTitle"
        :text="accordionText"
      />
    </div>
  </div>
</template>

<script>
import Accordion from './components/Accordion.vue';

export default {
  name: 'App',
  data() {
    return {
      accordionTitle: 'Accordion title',
      accordionText: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum."
    }
  },
  components: {
    Accordion
  }
}
</script>

<style>
  body {
    margin: 0;
    padding: 0;

    font-family: 'Roboto', sans-serif;
    font-size: 16px;
    color: #fff;
  }

  *,*::before,*::after {
    box-sizing: border-box;
  }

  h1,h2,h3,h4,h5,h6 {
    padding: 0;
    margin: 0;
  }
  
  p {
    padding: 0;
    margin: 0;
  }

  .wrapper {
    width: 100%;
    height: 100vh;
    background-color: #2C2C2C;
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
