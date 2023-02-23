<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld ref="hwRef" @get-data="getData"   
      @m-msg="(params) => { msg = params }" :msg="msg" /> -->
    <HelloWorld ref="hwRef" @get-data="getData" 
      v-model="msg">
      <template v-slot:header="goodlist">
        header

        {{ goodlist }}
      </template>

      dsadfadfasdf
      <el-tag type="primary">1222</el-tag>
    </HelloWorld>
    文本插值：<div>{{ counter }} {{ cpt_counterStr }}</div>
    原始html<div v-html="htmlStr"></div>
    <hr/>
    <!-- <div class="my-class" style="background-color: #f89;">属性绑定</div> -->
    <!-- <div class="my-class" :style="{backgroundColor: 'green'}">属性绑定</div> -->
    <div :class="true ? 'my-class' : 'other-class'" :style="{backgroundColor: 'green'}">属性绑定</div>
    <hr/>
    <button @click="toggleBtn">{{ btnName }}</button>

    <el-button>默认按钮</el-button>
  <el-button ref="btnDom" type="primary">主要按钮</el-button>

  <el-radio-group v-model="val_radio">
    <el-radio v-for="item in options_radio" :label="item.value" :key="item.value">{{ item.label }}</el-radio>
  </el-radio-group>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      counter: 0,
      htmlStr: '<span style="color: red;">hello vue!</span>',

      btnName: '打开',

      val_radio: undefined,
      options_radio: [
        {label: '选项1', value: '1'},
        {label: '选项2', value: '2'},
        {label: '选项3', value: '3'},
      ],
      msg: 'Welcome to Your Vue.js App',
    }
  },
  methods: {
    toggleBtn() {
      this.counter ++;
       console.log('val_radio', this.val_radio);
    },
    getData(goodlist) {
      console.log('子组件传递的数据', goodlist);
    }
  },
  computed: {
    cpt_counterStr() {
      return this.counter + '$';
    }
  },
  watch: {
    counter() {
      console.log('counter改变了');
    }
  },
  created() {
    
  },
  mounted() {
    console.log(this.$refs.hwRef.hello());
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
