<template>
  <div class="container">
    <loading v-if="isLoading"></loading>
    <global-header :user="user"></global-header>
    <router-view></router-view>
    <footer class="text-center py-4 text-secondary bg-light mt-6">
      <small>
        <ul class="list-inline mb-0">
          <li class="list-inline-item">© 2020 者也专栏</li>
          <li class="list-inline-item">课程</li>
          <li class="list-inline-item">文档</li>
          <li class="list-inline-item">联系</li>
          <li class="list-inline-item">更多</li>
        </ul>
      </small>
    </footer>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, computed } from "vue";
import { useStore } from "vuex";
import { DataProps } from "./store";
import "bootstrap/dist/css/bootstrap.min.css";
import GlobalHeader from "@/components/GlobalHeader.vue";
import Loading from '@/components/Loading.vue'
export default defineComponent({
  name: "App",
  components: {
    GlobalHeader,Loading
  },
  setup() {
    const store = useStore<DataProps>();
    const isLoading=computed(()=>store.state.isLoading)
    const user = computed(() => {
     return store.state.user
    });
    return {
      user,isLoading
    };
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
