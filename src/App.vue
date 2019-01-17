<template>
  <div id="app">
    <LoginPage/>
  </div>
</template>

<script>
import LoginPage from './components/LoginPage.vue';

export default {
  name: 'app',
  components: {
    LoginPage,
  },
};
</script>

<style>
@import 'https://rsms.me/inter/inter-ui.css';

*,
*::after,
**::before {
  box-sizing: border-box;
}
body {
  margin: 0;
  padding: 0;
  background: white;
  font-family: 'Inter UI', sans-serif;
}
::selection {
  background: #2D2F36;
}
::-webkit-selection {
  background: #2D2F36;
}
::-moz-selection {
  background: #2D2F36;
}
</style>
