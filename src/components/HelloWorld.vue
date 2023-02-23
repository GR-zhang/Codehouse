<template>
  <div class="hello">

    <slot name="header" :goodlist="goodlist" />

    <h1 @click="handleclick">{{ syncedvalue }}</h1>
    <el-button @click="() => { $emit('get-data', goodlist) }">发射事件</el-button>
    <el-button @click="syncedvalue = '2222' ">修改msg</el-button>


    <hr>
    插槽
    <slot />
    <hr>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    value: {
      type: String,
      // required: true,
      default: '2222'
    },
  
  },
  data() {
    return {
      goodlist: [1, 2, 3]
    }
  },
  methods: {
    hello() {
      console.log('子组件hello');
    },
    handleclick() {
      this.value = '222222';
    }
  },
  computed: {
    syncedvalue: {
      get() { return this.value },
      set(val) { this.$emit('input', val) }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
