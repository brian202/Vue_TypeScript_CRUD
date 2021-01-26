<template>
  <div id="app">
    <app-header/>
    <memo-app/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import AppHeader from './components/AppHeader.vue';
import MemoApp from '@/components/MemoApp.vue';

@Component({
  components: {
    AppHeader,
    MemoApp,
  }
})
export default class App extends Vue {

}
</script>

<style>
@import './styles/reset.css';

#app {
  width: 560px;
  margin: 0 auto;
}
</style>
