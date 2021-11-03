<template>
  <div class="hello">
    <h1 :class="{'changeColor': use}">{{ msg }}</h1>
    <input type="checkbox" v-model="use" id="r1">
    <h2 v-if="use">trueUse</h2>
    <h2 v-else>falseUse</h2>
    <h2>{{ readme() }}</h2>
    <div v-html="pMsg"></div>
    <div :id="use?divId:''" @click="clickDiv">qq</div>
    <a href="www.baidu.com" @click.prevent="onSubmit">baidu</a>
    <input type="text" v-model="msg">
    <p v-for="site in sites" :key="site.id">
      {{ site.id }}
    </p>
    <ul>
      <li v-for="(value, key, index) in object" :key="index">
        {{ key }} : {{ value }} : {{ index }}
      </li>
    </ul>
    <div @click.ctrl="msg = 1">Do something</div>
    <input v-model.lazy="msg" >
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      tit: '努力',
      pMsg: '<p>v-html添加内容</p>',
      use: false,
      divId: 'qqId',
      sites: [
        { id: 1 },
        { id: 2 },
        { id: 3 }
      ],
      object: {
        name: '菜鸟教程',
        url: 'http://www.runoob.com',
        slogan: '学的不仅是技术，更是梦想！'
      }
    }
  },
  methods: {
    readme: function () {
      return this.tit + '才会成功！'
    },
    clickDiv: function () {
      this.use = !this.use
    },
    onSubmit: function () {
      alert(this.msg)
    }
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  text-align: center;
  color: #2c3e50;
}
.changeColor {
  color: red;
}
h1, h2 {
  font-weight: normal;
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
