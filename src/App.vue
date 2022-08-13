<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <p style="text-align: center">
      <button @click="show = true">SHOW UP</button>
    </p>
    <HelloWorld v-if="show" msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import ErrorComponent from './components/ErrorComponent.vue';
import LoadingComponent from './components/LoadingComponent.vue';
const AsyncComp = function (resolve) {
  return {
    component: import('./components/HelloWorld.vue'),
    loading: LoadingComponent,
    error: ErrorComponent,
    delay: 200,
    timeout: 500,
  };
};

export default {
  name: 'App',
  components: {
    HelloWorld: AsyncComp,
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>
