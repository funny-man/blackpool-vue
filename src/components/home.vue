<template>
  <div>
    <!--导航条-->
    <nav id="navbar">
      <div class="navbar-warpper">
        <div class="nav nav-logo">
          <a href="#home" class="logo"></a>
        </div>
        <div class="nav nav-button">
          <ul class="clearfix">
            <li class="sign-in"><a href="#">{{!english?'登录':'Sign in'}}</a></li>
            <li><a href="#">|</a></li>
            <li class="sign-up"><a href="#">{{!english?'注册':'Sign up'}}</a></li>
            <li class="en" @click="switchLanguage"><a href="#">中/EN</a></li>
          </ul>
        </div>
      </div>
    </nav>
    <!--首页-->
    <header id="home">
      <div class="layout clearfix">
        <div class="intro-img"></div>
        <div class="intro-text">
          <transition name="banner">
            <div v-show="bannerShow">
              <h1>BlackPool</h1>
              <h2>Focusing on Mining and Staking</h2>
            </div>
          </transition>
          <a href="#services" class="btn">Sign in</a>
        </div>
      </div>
    </header>
    <!--blackpool矿池-->
    <section class="black－pool">
      <div class="layout">
        <div class="title">
          <h3>{{english?'BlackPool Staking Pool':'BlackPool 矿池'}}</h3>
          <h4>{{english?'Delegate your tokens to BlackPool and earn rewards':'使用您的token投票，获取收益'}}</h4>
        </div>
        <div class="content min-w" ref="card">
          <transition name="blackpool">
            <ul v-if="blackpoolShow">
              <li v-for="(item,index) in blackPoolData" :key="index" :class="item.state ? 'blue-border':'gray-border'">
                <img class="icon" width="60px" height="60px" :src="item.icon" alt="">
                <div class="item-val">{{item.value}}</div>
                <div class="item-name">{{item.name}}</div>
                <button class="item-btn" :class="{'is-disabled':!item.state}" type="button" :disabled="!item.state" @click="showBox(index)">{{english?item.btnEnglishText:item.btnText}}</button>
              </li>
            </ul>
          </transition>
        </div>
      </div>
    </section>
    <section class="black－pool superiority">
      <div class="layout">
        <div class="title">
          <h3>{{english?'Advantage':'优势'}}</h3>
          <h4>{{english?'Delegate your tokens and get the best service':'委托您的token并获得优质服务'}}</h4>
        </div>
        <div class="content">
          <div class="card-warpper">
            <div class="card">
              <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_1.png" alt="">
              <div class="card-text">
                <h5>{{english?'Double Protection':'双重保护'}}</h5>
                <p>{{english?'Security isolation mechanism. Specialized private key and server management':'隔离机制，私钥与服务器专业保护'}}</p>
              </div>
            </div>
            <div class="card">
              <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_2.png" alt="">
              <div class="card-text">
                <h5>{{english?'7*24 Online':'7*24小时在线'}}</h5>
                <p>{{english?'Experienced technical team support Automatic monitoring':'专业技术团队维护'}}</p>
              </div>
            </div>
            <div class="card">
              <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_3.png" alt="">
              <div class="card-text">
                <h5>{{english?'Community Governance':'社区治理'}}</h5>
                <p>{{english?'Contribute to the governance by integrating industry resources':'业内上下游资源整合，参与社区贡献'}}</p>
              </div>
            </div>
            <div class="card">
              <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_4.png" alt="">
              <div class="card-text">
                <h5>{{english?'High Standard':'行业高标准'}}</h5>
                <p>{{english?'Higher specification of hardware and software than industry  requirements':'比行业专有要求更高规格的软硬件性能'}}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!--关于-->
    <section class="about">
      <div class="layout clearfix">
        <img class="icon" width="378px" src="../assets/image/about.png" alt="">
        <div class="about-text">
          <h5>{{english?'About BlackPool':'关于 BlackPool'}}</h5>
          <p>{{english? 'BlackPool is a blockchain service platform focusing on mining and staking economy, we are devoting ourself to connect users to the blockchain world conveniently.' : 'BlackPool是一家专注于加密货币挖矿和staking经济的区块链服务平台。 我们致力于让用户便捷地连接到区块链世界。让每一个人都可以分享到区块链带来的红利。'}}</p>
        </div>
      </div>
    </section>
    <!--合作-->
    <section class="network">
      <div class="layout clearfix">
        <div class="title">
          <h3>{{english?'Partners of BlackPool':'合作伙伴'}}</h3>
        </div>
        <div class="content">
          <img class="logo" width="146px" src="../assets/image/logo/logo_1.png" alt="">
          <img class="logo" width="146px" src="../assets/image/logo/logo_2.png" alt="">
          <img class="logo" width="146px" src="../assets/image/logo/logo_3.png" alt="">
          <img class="logo" width="146px" src="../assets/image/logo/logo_4.png" alt="">
          <img class="logo" width="146px" src="../assets/image/logo/logo_5.png" alt="">
        </div>
      </div>
    </section>
    <!--联系方式-->
    <section id="a" class="contact">
      <div class="layout clearfix">
        <div class="content">
          <a target="_blank" href="https://twitter.com/BlackPo17368543"><img class="logo" width="26px" src="../assets/image/app/t.png" alt=""></a>
          <a href="#a"><img class="logo" width="26px" src="../assets/image/app/w.png" alt=""></a>
          <a href="#a"><img class="logo" width="26px" src="../assets/image/app/f.png" alt=""></a>
          <a target="_blank" href="https://weibo.com/p/1005057143515164"><img class="logo" width="26px" src="../assets/image/app/x.png" alt=""></a>
          <a target="_blank" href="https://t.me/joinchat/AAAAAFatTrYKotlevENm0A"><img class="logo" width="26px" src="../assets/image/app/tt.png" alt=""></a>
          <a href="Mailto:bonnie@coc.vc"><img class="logo" width="26px" src="../assets/image/app/e.png" alt=""></a>
        </div>
      </div>
    </section>
    <!--联系我们-->
    <section class="contact backdrop">
      <div class="layout">
        <form action="/getinfo" method="get">
          <div class="clearfix">
            <div class="form-md form-one">
              <div class="form-group group-left">
                <div class="placeholder">{{english?'NAME':'请输入您的名字'}}</div> 
                <input v-model="username" class="form-control formtext" id="username" type="text" name="username" value="">
              </div>
              <div class="form-group group-right">
                <div class="placeholder">{{english?'CONTACT INFORMATION':'请输入您的邮箱地址或电话号码'}}</div>
                <input v-model="email" class="form-control formtext" id="email" type="text" name="email">
              </div>
            </div>
            <div class="form-md form-two">  
              <div class="textarea">
                <div class="placeholder">{{english?'CORPORATION INTENTION':'请填写您需要合作的内容'}}</div>
                <textarea v-model="message" class="form-control message" id="message" required="" data-validation-required-message="Please enter a message." aria-invalid="false"></textarea>
              </div>
            </div>  
          </div>
          <a :href="'Mailto:bonnie@coc.vc?Subject=blackpool&amp;Body='+emailBody" class="btn">{{english?'Submit':'提 交'}}</a>
        </form>
      </div>
    </section>
    <modal-box ref="box" :data="blackPoolData"></modal-box>

  </div>
</template>

<script>
//如果是动态数据下面的所需的icon通过请求blackPoolData的时候获得
import iost from "../assets/image/blackpool/iost.png";
import iotex from "../assets/image/blackpool/iotex.png"
import bos from "../assets/image/blackpool/bos.png"
import decred from "../assets/image/blackpool/decred.png"
import livepeer from "../assets/image/blackpool/livepeer.png"
import horizen from "../assets/image/blackpool/horizan.png"

import ModalBox from '../base/modal_box.vue'

export default {
  name: 'Home',
  props: {
  },
  data() {
    return {
      english: false,
      bannerShow: false,
      blackpoolShow: false,
      blackPoolData: [
        {
          icon: iost,
          name: 'IOST',
          btnText: '委托',
          btnEnglishText: 'Delegate',
          value: '8.1%~17.1%',
          state: true,
          text: [
            {
              title: '1.IOST官方投票',
              content: '安装谷歌插件钱包iwallet，并导入您的IOST账号，使用Chrome浏览器打开IOST官方投票页面，搜索BlackPool投票'
            },
            {
              title: '2.TokenPocket钱包投票',
              content: '下载TokenPocket钱包，注册IOST钱包,在资产页面，点击投票，搜索BlackPool，输入投票数并确认投票成功。在该页面可以领取每日奖励和季度奖励。'
            },
            {
              title: '3.Biss交易所投票',
              content: '打开Biss交易所投票页面,在搜索栏搜索BlackPool，并点击投票'
            }
          ],
          prompt:'注意：因IOST主网升级，充值与投票过程请注意区分ERC20地址和IOST主网地址'
        },
        {
          icon: iotex,
          name: 'IOTEX',
          btnText: '委托',
          btnEnglishText: 'Delegate',
          value: '7%~15%',
          state: true,
          text: [
            {
              title: '1.使用Chrome安装MetaMask，导入存放了IOTX的钱包，钱包中需要有少量ETH支付投票过程中的gas费用',
              content: ''
            },
            {
              title: '2.前往IOTEX官方投票页面，点击banner处立即投票',
              content: ''
            },
            {
              title: '3.节点名称搜索BlackPool，输入所投IOTX数量，选择投票时长获取额外票数，建议开启自动质押，填好信息后确认投票',
              content: ''
            },
            {
              title: '4.在MetaMask确认两笔交易，两笔交易均成功后则投票成功',
              content: ''
            }
          ],
          prompt:''
        },
        {
          icon: bos,
          name: 'BOS',
          btnText: '委托',
          btnEnglishText: 'Delegate',
          value: '8.1%~17.1%',
          state: true,
          text: [
            {
              title: '1.在Chrome浏览器使用Scatter登陆官方投票网站',
              content: ''
            },
            {
              title: '2.节点账号搜索BlackPool',
              content: ''
            },
            {
              title: '3.勾选BlackPool名字前的方块，点击投票',
              content: ''
            }
          ],
          prompt:''
        },
        {
          icon: decred,
          name: 'Decred',
          btnText: '敬请期待',
          btnEnglishText: 'Coming',
          value: '8.1%~17.1%',
          state: false,
          prompt:''
        },
        {
          icon: livepeer,
          name: 'LivePeer',
          btnText: '敬请期待',
          btnEnglishText: 'Coming',
          value: '8.1%~17.1%',
          state: false,
          prompt:''
        },
        {
          icon: horizen,
          name: 'Horizen',
          btnText: '敬请期待',
          btnEnglishText: 'Coming',
          value: '8.1%~17.1%',
          state: false,
          prompt:''
        }
      ],
      email: '',
      username: '',
      message: ''
    }
  },
  computed: {
    emailBody:function() {
      return `
        姓名: ${this.username}
        邮箱或电话: ${this.email}
        合作内容: ${this.message}
      `
    }
  },
  mounted() {
    this.bannerShow = true
    window.document.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    switchLanguage() {
      this.english = !this.english
    },
    showBox(index) {
      this.$refs.box.show(index)
    },
    handleScroll() {
      // let clock
      // if(clock){
      //   clearTimeout(clock)
       
      // }
      // clock=setTimeout(function(){
        
      // },300);
      // console.log('滚');
      let scrollTop = document.documentElement.scrollTop? document.documentElement.scrollTop:window.pageYOffset 
      // console.log(scrollTop);
      let windowHeight = window.innerHeight 
      // console.log(windowHeight);
      let offsetTop=this.$refs.card.offsetTop+200
      // console.log(offsetTop);
      if(offsetTop<windowHeight+scrollTop){
        this.blackpoolShow = true
      } else {
         this.blackpoolShow = false
      }
    }
  },
  components: {
    ModalBox
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  scoped lang="scss">
/*清除浮动*/
.clearfix:after {
  content: '';
  display: block;
  clear: both;
}
nav {
  box-shadow: 0 0 10px 0 rgba(195,195,195,0.50);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #fff;
  z-index: 1;
}
.navbar-warpper {
  background-color: #fff;
  height: 56px;
  margin: 0 auto;
  max-width: 1200px;
  .nav {
    display: inline-block;
    width: 50%;
    box-sizing: border-box;
  }
  .nav-logo {
    padding-left:24px;
    .logo {
      display: inline-block;
      width: 146px;
      margin: 13px 0;
      height: 30px;
      background-image: url("../assets/logo.png");
      background-position: center;
      background-size:contain;
      background-repeat: no-repeat;
      float: left;
    }
  }
  .nav-button {
    padding-right:24px;
    font-size: 14px;
    ul {
      float: right;
      li {
        display: inline-block;
        a {
          line-height: 56px;
          color: #1B1B1B;
        }
      }
      .sign-in {
        padding-right: 12px;
      }
      .sign-up {
        padding-left: 12px;
      }
      .en {
        padding-left: 86px;
      }
    }
  } 
}
#home {
  margin-top: 56px;
  height: 546px;
  background-image: url("../assets/image/bg.png");
  background-position: center;
  background-size:10px;
  // background-repeat: no-repeat;
  .layout {
    margin: 0 auto;
    max-width: 1200px;
    min-width: 1120px;
    box-sizing: border-box;
    padding: 74px 120px;
  }
  .intro-img {
    float: left;
    width: 398px;
    padding-top: 398px;
    // background-color: pink;
    background-image: url("../assets/image/el.png");
    background-position: center;
    background-size:contain;
    background-repeat: no-repeat;
  }
  .intro-text {
    text-align: left;
    float: right;
    margin: 123px 0;
    h1 {
      font-size: 52px;
      color: #1B1B1B;
      // font-family: Arial-BoldMT;
      letter-spacing: 2.26px;
      font-weight:700;
    }
    h2 {
      // font-family: ArialMT;
      font-size: 26px;
      color: #418FF4;
      letter-spacing: 3px;
      margin-top: 6px;
    }
    a {
      display: inline-block;
      background-color: #418FF4;
      border: 1px solid #2973D3;
      font-family: PingFangSC-Regular;
      font-size: 16px;
      color: #FFFFFF;
      letter-spacing: 0.7px;
      padding: 9px 34px;
      border-radius: 2px;
      margin-top: 32px;
    }
  }
}
.black－pool {
  .layout {
    margin: 0 auto;
    max-width: 1200px;
    // min-width: 1120px;
    box-sizing: border-box;
    padding: 78px 0 66px 0;
    text-align: center;
    .title {
      font-size: 32px;
      font-weight: 700;
      color: #1B1B1B;
      letter-spacing: 1.39px;
      text-align: center;
      h4 {
        font-size: 14px;
        color: #707070;
        letter-spacing: 0.61px;
        text-align: center;
        margin-top: 6px;
      }
    }
    .min-w {
      min-height: 634px;
    }
    .content {
      ul {
        display: inline-block;
        max-width: 987px;
        margin-left: -140px;
        li {
          margin-left: 140px;
          padding: 20px 0;
          display: inline-block;
          width: 187px;
          margin-top: 76px;
          .item-val {
            font-size: 20px;
            color: #006FFF;
            letter-spacing: 0.87px;
            text-align: center;
            font-weight: 700;
            margin-top: 26px;
          }
          .item-name {
            font-size: 14px;
            color: #1B1B1B;
            letter-spacing: 0.61px;
            text-align: center;
            margin-top: 22px;
          }
          .item-btn {
            background-color: #418FF4;
            border: 1px solid #2973D3;
            color: #FFF;
            font-size: 14px;
            padding: 8px 40px;
            margin-top: 16px;
            border-radius: 2px;
            outline: none;
            &:hover,
            &:focus {
              background-color: rgb(50, 129, 233);
            }
            &:active {
              background-color: rgb(73, 149, 248);
            }
            &.is-disabled {
              cursor:not-allowed;
              &,
              &:hover,
              &:focus,
              &:active {
                background: #BEBEBE;
                border: 1px solid #989898;
              }
            } 
          }
        }
        .blue-border {
          border: 1px solid #418FF4;

        }
        .gray-border {
          border: 1px solid #E7E7E7;
        }
      }
      .card-warpper {
        display: inline-block;
        max-width: 980px;
        margin-left: -70px;
        .card {
          margin-left: 70px;
          padding: 20px 0;
          display: inline-block;
          box-sizing: border-box;
          width: 420px;
          margin-top: 60px;
          padding: 10px;
          text-align: left;
          .icon {
            float: left;
          }
          .card-text {
            margin-left: 120px;
            margin-top: 24px;
            vertical-align: middle;
            h5 {
              font-size: 18px;
              color: #1B1B1B;
              letter-spacing: 0;
            }
            p {
              font-size: 14px;
              color: #AEAEAE;
              letter-spacing: 0;
              margin-top: 16px;
            }
          }
        }
      }
    }
  }
}
.superiority {
  border-top: 1px dashed #C9C9C9;
}
.about {
  background-color: #F6FCFF;
  .layout {
    margin: 0 auto;
    max-width: 1200px;
    // min-width: 1120px;
    box-sizing: border-box;
    padding: 100px 0;
    text-align: center;
    .icon {
      float: left;
      margin-left: 140px;
    }
    .about-text {
      text-align: left;
      margin: 60px 100px 0 588px;
      h5 {
        font-size: 32px;
        color: #1B1B1B;
        letter-spacing: 1.39px;
        font-weight: 700;
      }
      p {
        font-size: 14px;
        color: #707070;
        letter-spacing: 0.61px;
        margin-top: 8px;
      }
    }
  }
}
.network {
  .layout {
    margin: 0 auto;
    max-width: 1200px;
    // min-width: 1120px;
    box-sizing: border-box;
    padding: 90px 0 120px 0;
    text-align: center;
    .title {
      font-size: 32px;
      font-weight: 700;
      color: #1B1B1B;
      letter-spacing: 1.39px;
      text-align: center;
    }
    .content {
      margin-top: 66px;
      .logo {
        margin: 20px 40px;
      }
    }
  }
}
.contact {
  background-color: #F6FCFF;
  &.backdrop {
      background-color: #FFF;
      .layout {
        padding: 0 20px;
      }
  }
  .layout {
    margin: 0 auto 90px auto;
    max-width: 1200px;
    // min-width: 1120px;
    box-sizing: border-box;
    padding: 10px 0;
    text-align: center;
    .content {
      .logo {
        margin: 0 40px;
      }
    }
    form {
      .form-md {
        max-width: 714px;
        margin: 0 auto;
        &.form-one {
          margin-top: 40px;
        }
        .form-group {
          display: inline-block;
          width: 50%;
          padding: 20px 11px;
          box-sizing: border-box;
          &.group-left {
            padding-left: 0;
          }
          &.group-right {
            padding-right: 0;
          }
        }
      }
      a {
        display: inline-block;
        margin-top: 28px;
        background-color: #418FF4;
        border: 1px solid #2973D3;
        font-family: PingFangSC-Regular;
        font-size: 16px;
        color: #FFFFFF;
        letter-spacing: 0.7px;
        padding: 9px 34px;
        border-radius: 2px;
        margin-top: 32px;
      }
      .form-control {
        display: block;
        box-sizing: border-box;
        width: 100%;
        padding: 7px;
        font-size: 14px;
        color: #555;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 3px;
        margin-top: 10px;
        // margin: 10px auto 20px auto;
        outline-color: #418FF4;
      }
      .placeholder {
        text-align: left;
        font-size: 12px;
        color: #B9BEC2;
      }
      .formtext {
        // max-width: 346px;
        // margin-left: 0;
        // margin-right: 0;
      }
      .message {
        // max-width: 714px;
        min-height: 142px;
      }
    }
  }
}
.banner-enter-active, .banner-leave-active {
  transition: all 1s ease;
}
.banner-enter, .banner-leave-to {
  opacity: 0;
  transform: translateY(70px);
}
.blackpool-enter-active, .blackpool-leave-active {
  transition: all 1s ease;
}
.blackpool-enter, .blackpool-leave-to {
  opacity: 0;
  transform: translateY(70px);
}
</style>
