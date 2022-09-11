<script setup>
import WelcomeItem from "../WelcomeItem.vue";
</script>

<template>
  <WelcomeItem>
    <template #icon
      ><!--template para el esqueleto-->
      <ToolingIcon />
    </template>
    <template #heading>Tooling</template>

    This project is served and bundled with
    <a href="https://vitejs.dev/guide/features.html" target="_blank">Vite</a>.
    The recommended IDE setup is
    <a href="https://code.visualstudio.com/" target="_blank">VSCode</a> +
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>.
    If you need to test your components and web pages, check out
    <a href="https://www.cypress.io/" target="_blank">Cypress</a> and
    <a href="https://on.cypress.io/component" target="_blank"
      >Cypress Component Testing</a
    >.

    <br />

    More instructions are available in <code>README.md</code>.
  </WelcomeItem>
</template>
