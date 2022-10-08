<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div :class="['box',{'dark':dark}]"></div>
    <button @click="changeColor">切换颜色</button>
    <hr><br>
    <div class="header" @click="changeTheme">header</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      dark:false  
    }
  },
  methods: {
    changeColor(){
      this.dark = !this.dark;
    },
    changeTheme () {
        document.documentElement.setAttribute('data-theme', 'theme1')
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../assets/css/mixin";
.dark{
  --theme-color: #eee;
  --theme-background: rgb(29, 29, 29);
}
/* 更改pink类名下变量的取值 */
.pink{
  --theme-color: #fff;
  --theme-background: pink;
}

.box {
  margin: 0 auto;
  transition: all .2s;
  width: 100px;
  height: 100px;
  border: 1px solid #000;
  /* 使用变量 */
  color: var(--theme-color);
  background: var(--theme-background);
  margin-bottom: 40px;
}

.header{
  width: 100%;
  height: 100px;
  @include bg_color();
}

</style>
