<!--
 * @Author: wangzhongjie
 * @Date: 2020-04-20 09:34:43
 * @LastEditors: wangzhongjie
 * @LastEditTime: 2020-04-20 14:51:01
 * @Description: 输入框
 * @Email: UvDream@163.com
 -->
<template>
  <div>
    <input :type="type" v-model="value" @change="inputChange" />
  </div>
</template>
<script>
export default {
  props: {
    type: String,
    value: {}
  },
  setup(props, { emit }) {
    const inputChange = e => {
      console.log(e.target.value);
      emit("input", e.target.value);
    };
    console.log(props);
    return { props, inputChange };
  }
};
</script>
