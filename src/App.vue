<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>
    <h1>ts+vue3测试</h1>
  </div>
  <button v-for="(t, i) in btns" :key="i" @click="selectWayFun(i)">
    {{ t }}
  </button>
  <h2>{{ seletWay }}</h2>
</template>

<script lang="ts">
import {
  reactive,
  toRefs,
  onMounted,       // 组件挂载完成后执行的函数
  onBeforeMount,   // 组件挂载到节点之前执行的函数
  onBeforeUpdate,  // 组件更新之前执行的函数
  onUpdated,       // 组件更新完成之后执行的函数 
} from "vue";

export default {
  name: "App",
  // setup函数代替了data和methods属性，将变量和方法直接写进去便可以使用，但必须使用return 返回
  // ref函数: 生成响应式对象
  // reactive函数: 生成响应式对象
  // toRefs函数
  setup() {
    interface DataProps {
      btns: string[];
      seletWay: string;
      selectWayFun: (i: number) => void;
    }
    const data: DataProps = reactive({
      btns: ["学习", "测试", "工作", "睡觉"],
      seletWay: "",
      selectWayFun: (index: number) => {
        data.seletWay = data.btns[index];
        console.log(111)
      },
    });
    const refData = toRefs(data);
    return { ...refData };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
