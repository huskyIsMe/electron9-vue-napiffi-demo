<template>
  <div id="app">
    测试：
    libpath：{{libpath}}
    计算结果：{{res}}
  </div>
</template>
<script>
const path = require('path')
const ffi = require('ffi-napi')
//打包时候使用
const dllPath = path.resolve('resources/dll/Dll1.dll')
//dev时候使用
// const dllPath = path.resolve('public/dll/Dll1.dll')
const myDll = ffi.Library(dllPath, {
  funAdd: ['int', ['int', 'int']]
})

export default {
  data () {
    return {
      libpath: '',
      res: ''
    }
  },
  created () {
    this.test()
  },
  methods: {
    test () {
      console.log('开始测试')
      console.log('libpath', dllPath)
      this.libpath = dllPath

      const a = parseInt(2)
      const b = parseInt(3)
      const res = myDll.funAdd(a, b)
      this.res = res
      console.log('计算结果:' + res)
    }
  }
}
</script>

<style lang="stylus">
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>
