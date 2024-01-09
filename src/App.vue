<template> 
  <MainComponent msg="This is Vue main app" :styles="styles" />
</template>

<script>
import MainComponent from "./components/main-component.vue";

export default {
  id: "app",
  name: "App",
  components: {
    MainComponent,
  },
  data() {
    return {
      theme: null,
      styles: null
    };
  },
  watch: {
    theme() {
      const getBackgroundColor = () => {
        switch (this.theme) {
          case "blue":
            return "#9BBEC8";
          case "green":
            return "#93B1A6";
          default:
            return "initial";
        }
      };
      this.styles = {
        height: '100%',
        padding: "20px",
        color: "white",
        background: getBackgroundColor()
      };
    },
  },
  mounted() {
    this.theme = 'blue';
    this.handleThemeChange = this.handleThemeChange.bind(this);
    window.addEventListener("changeTheme", this.handleThemeChange);
  },
  beforeUnmount() {
    window.removeEventListener("changeTheme", this.handleThemeChange);
  },
  methods: {  
    handleThemeChange(evt) {
      this.theme = evt.detail.theme;
    },
  },
};
</script>

<style>
  #app {
    margin-top: 60px;
  }
</style>
