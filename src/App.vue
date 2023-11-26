<script setup>
  import {
    RouterView
  } from 'vue-router'
</script>

<template>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">


    <nav>
      <RouterLink to="/">
        <p>Home</p>
      </RouterLink>
      <RouterLink to="/about">
        <p>About</p>
      </RouterLink>
    </nav>

  <RouterView />
</template>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    font-family: 'Poppins', sans-serif;
    background-color: #dddd;
  }

  nav {
    background-color: #fff;
    height: 70px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 10px;
    margin-bottom: 25px;
    border-top: 2px solid #0984e3;
    box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
    -webkit-box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
  }
  nav a {
    text-decoration: none;
    color: black;
  }
  nav p {
    text-decoration: none;
  }
</style>