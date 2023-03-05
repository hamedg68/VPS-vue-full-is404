<template>
  <div class="layout">
    <div class="navigation">
      <div style="text-align: center;">is404: {{ pageContext.is404 }}</div>
      <button @click="navigate1">page1</button>
      <button @click="navigate2">page2</button>
      <button @click="navigate3">page3</button>
      <button @click="navigate4">page4</button>
      <a href="/" class="logo">
        <img src="./logo.svg" height="64" width="64" />
      </a>
      <Link href="/">Welcome</Link>
      <Link href="/markdown">Markdown</Link>
      <Link href="/star-wars">Data Fetching</Link>
      <Link href="/hello">Routing</Link>
    </div>
    <div class="content"><slot /></div>
  </div>
</template>

<script lang="ts" setup>
import Link from './Link.vue'
import { PageContext } from './types';
import { usePageContext } from './usePageContext';
import { navigate } from 'vite-plugin-ssr/client/router'

const pageContext = usePageContext() as PageContext


const navigate1 = () => {
  navigate('/')
}
const navigate2 = () => {
  navigate('/markdown')
}
const navigate3 = () => {
  navigate('/star-wars')
}
const navigate4 = () => {
  navigate('/hello/alice')
}

</script>

<style>
body {
  margin: 0;
  font-family: sans-serif;
}
* {
  box-sizing: border-box;
}
a {
  text-decoration: none;
}
code {
  font-family: monospace;
  background-color: #eaeaea;
  padding: 3px 5px;
  border-radius: 4px;
}
</style>

<style scoped>
.layout {
  display: flex;
  max-width: 900px;
  margin: auto;
}
.content {
  padding: 20px;
  padding-bottom: 50px;
  min-height: 100vh;
}
.navigation {
  padding: 20px;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  line-height: 1.8em;
  border-right: 2px solid #eee;
}
.logo {
  margin-top: 20px;
  margin-bottom: 10px;
}
.content {
  transition: opacity 0.1s ease-in;
}
.content.page-transition {
  opacity: 0;
}
</style>
