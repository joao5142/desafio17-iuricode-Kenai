<template>
  <router-view />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Mukta:wght@700&family=Open+Sans:ital,wght@0,400;0,600;1,300&display=swap");
/*##RESET*/
* {
  box-sizing: border-box;
  padding: 0px;
  margin: 0px;
}

ul,
ol {
  list-style: none;
}

a {
  text-decoration: none;
}

img {
  height: auto;
}

button,
input,
textarea {
  border: 0;
  outline: none;
}

button:focus,
input:focus,
textarea:focus {
  border: 0;
  outline: none;
}
li {
  cursor: pointer;
}
body {
  font-family: "Open Sans", sans-serif;
  overflow: hidden;
  background-color: $dark-color;
  color: $white-color;
  overflow-y: auto;
}
body::-webkit-scrollbar {
  max-width: 10px;
}
body::-webkit-scrollbar-track {
  background: $white-color;
}
body::-webkit-scrollbar-thumb {
  background: $gray-dark-color;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>
