<template>
  <div class="home">
    {{ message }}
    <div>
      <p>基础</p>
      <button @click="addFunc">+</button>
      {{ count }}
      <button @click="lessFunc">-</button>
      {{ computeCount }}
    </div>
    <div>
      组件
      <JInput :type="data.type" :value="count" />
    </div>
  </div>
</template>

<script>
import {
  ref,
  onMounted,
  onBeforeMount,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  onErrorCaptured,
  reactive,
  computed
} from "vue";
import JInput from "../components/input";
export default {
  name: "Home",

  setup() {
    const data = reactive({
      type: "number"
    });
    // ref==useState
    const count = ref(0);
    // const val = ref("输入框初始化");
    const addFunc = () => {
      count.value++;
    };
    const lessFunc = () => {
      count.value--;
    };
    // computed
    const computeCount = computed(() => count.value * 10);
    onMounted(() => {
      console.log("mounted -> onMounted");
    });
    onBeforeMount(() => {
      console.log("beforeMount -> onBeforeMount");
    });
    onUpdated(() => {
      console.log("updated -> onUpdated");
      console.log(count.value);
    });
    onBeforeUnmount(() => {
      console.log("beforeDestroy -> onBeforeUnmount");
    });
    onUnmounted(() => {
      console.log("destroyed -> onUnmounted");
    });
    onErrorCaptured(() => {
      console.log("errorCaptured -> onErrorCaptured");
    });
    return { message: "hello", addFunc, lessFunc, count, data, computeCount };
  },
  components: { JInput }
};
</script>
