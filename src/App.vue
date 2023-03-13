<template>
  <header>
    <router-link to="/">
      <h1>
        <span>Data</span>
        Story
      </h1>
    </router-link>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
  /* background-color: #42b883; */
}

body{
  background-color: #34595E;
}

a{
  text-decoration: none;
}

header{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background-color: 0px 0px 6px rgba(0, 0, 0, 0.1);
}

h1{
  color: white;
  font-size: 17px;
  font-size: 28px;
}

span{
  color: #42b883;
}

</style>
