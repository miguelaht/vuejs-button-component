<template>
  <h3>Default</h3>
  <Button startIcon="local_grocery_store" endIcon="face" v-bind:isActive="false"/>
  <Button startIcon="local_grocery_store" endIcon="face" size="md"/>
  <Button startIcon="local_grocery_store" endIcon="face" size="lg"/>
  <Button startIcon="local_grocery_store" endIcon="face" size="xl"/>
  <h3>outline</h3>
  <Button variant="outline" />
  <h3>text</h3>
  <Button variant="text" />
  <h3>primary no shadow</h3>
  <Button color="primary" v-bind:hasShadow="false" />
  <h3>secondary</h3>
  <Button color="secondary" />
  <h3>danger</h3>
  <Button color="danger" />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Button from "./components/Button.vue";

@Options({
  components: {
    Button,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
