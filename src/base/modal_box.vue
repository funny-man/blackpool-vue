<template>
  <div id="box" v-show="showFlag" @click="hide">
    <div class="panel" @click.stop>
      <div class="title">
        <img class="logo" width="60px" :src="data[index].icon" alt="">
        <h5 class="name">{{data[index].name}}</h5>
        <img class="close" width="20px" src="../assets/image/close.png" alt="" @click="hide">
      </div>
      <div class="content">
        <div class="item" v-for="(item,index) in data[index].text" :key="index">
          <h5 v-html="item.title"></h5>
          <p v-for="(text,index) in item.content" :key="index" v-html="text"></p>
        </div>
        <div class="prompt">{{data[index].prompt}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalBox',
  props: {
    data:{
      type: Array,
      default: function(){return []}
    }
  },
  data() {
    return {
      showFlag: false,
      index: 0
    }
  },
  methods: {
    show(index) {
      this.showFlag = true
      this.index = index
    },
    hide() {
      this.showFlag = false
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  scoped lang="scss">

#box {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 2;
  background: rgba(67,67,67,0.51);
  .panel {
    width: 50%;
    height: 80%;
    background-color: #F6FCFF;
    border-radius: 10px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    .title {
      text-align: left;
      position: relative;
      .logo {
        display: inline-block;
        margin: 20px 14px 20px 56px;
        vertical-align: middle;
      }
      .name {
        display: inline-block;
        display: inline-block;
        line-height: 100px;
        vertical-align: middle;
      }
      .close {
        position: absolute;
        right: 20px;
        top: 20px;
      }
    }
    .content {
      background-color: #fff;
      position: absolute;
      top: 100px;
      left: 0;
      right: 0;
      bottom: 0;
      border-radius: 0 0 10px 10px;
      text-align: left;
      padding: 2px 56px 30px 56px;
      overflow-y: auto;
      font-size: 14px;
      color: #1B1B1B;
      letter-spacing: 3.15px;
      line-height: 30px;
      .item {
        margin-top: 10px;
        margin-top: 34px;
      }
      .prompt {
        margin-top: 34px;
        color: #D84343;
      }
    }
  }
}
</style>
