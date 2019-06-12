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
            <li class="en" @click="switchLanguage"><a href="javascript:volid(0);">中/EN</a></li>
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
        <div class="content blackpool-min-h" ref="card">
          <transition name="blackpool">
            <ul v-show="blackpoolShow">
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
    <!--优势-->
    <section class="black－pool superiority">
      <div class="layout">
        <div class="title">
          <h3>{{english?'Advantage':'优势'}}</h3>
          <h4>{{english?'Delegate your tokens and get the best service':'委托您的token并获得优质服务'}}</h4>
        </div>
        <div class="content card-min-h" ref="superiority">
          <div class="card-warpper">
            <transition name="card1">
              <div v-show="cardShow" class="card">
                <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_1.png" alt="">
                <div class="card-text">
                  <h5>{{english?'Double Protection':'双重保护'}}</h5>
                  <p>{{english?'Security isolation mechanism. Specialized private key and server management':'隔离机制，私钥与服务器专业保护'}}</p>
                </div>
              </div>
            </transition>
            <transition name="card2">
              <div v-show="cardShow" class="card">
                <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_2.png" alt="">
                <div class="card-text">
                  <h5>{{english?'7*24 Online':'7*24小时在线'}}</h5>
                  <p>{{english?'Experienced technical team support Automatic monitoring':'专业技术团队维护,全自动监控'}}</p>
                </div>
              </div>
            </transition>
            <transition name="card3">
              <div v-show="cardShow" class="card">
                <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_3.png" alt="">
                <div class="card-text">
                  <h5>{{english?'Community Governance':'社区治理'}}</h5>
                  <p>{{english?'Contribute to the governance by integrating industry resources':'业内上下游资源整合，参与社区贡献'}}</p>
                </div>
              </div>
            </transition>
            <transition name="card4">
              <div v-show="cardShow" class="card">
                <img class="icon" width="104px" height="104px" src="../assets/image/icons/icon_4.png" alt="">
                <div class="card-text">
                  <h5>{{english?'High Standard':'行业高标准'}}</h5>
                  <p>{{english?'Higher specification of hardware and software than industry  requirements':'比行业专有要求更高规格的软硬件性能'}}</p>
                </div>
              </div>
            </transition>
          </div>
        </div>
      </div>
    </section>
    <!--关于-->
    <section class="about">
      <div class="layout clearfix" ref="aboutDom">
        <transition name="about-left">
          <img v-show="aboutShow" class="icon" width="378px" src="../assets/image/about.png" alt="">
        </transition>
        <transition name="about-right">
          <div v-show="aboutShow" class="about-text">
            <h5>{{english?'About BlackPool':'关于 BlackPool'}}</h5>
            <p>{{english? 'BlackPool is a blockchain service platform focusing on mining and staking economy, we are devoting ourself to connect users to the blockchain world conveniently.' : 'BlackPool是一家专注于加密货币挖矿和staking经济的区块链服务平台。 我们致力于让用户便捷地连接到区块链世界。让每一个人都可以分享到区块链带来的红利。'}}</p>
          </div>
        </transition>
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
          <a href="javascript:volid(0);">
            <img class="logo wx-logo" width="26px" src="../assets/image/app/w.png" alt="">
            <div class="qrcode">
              <img width="200px" src="../assets/qrcode.jpg" alt="">
            </div>
          </a>
          <!-- <a href="javascript:volid(0);"><img class="logo" width="26px" src="../assets/image/app/f.png" alt=""></a> -->
          <a target="_blank" href="https://twitter.com/BlackPo17368543"><img class="logo" width="26px" src="../assets/image/app/x.png" alt=""></a>
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
    <modal-box ref="box" :data="blackPoolData" :english="english"></modal-box>

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
      cardShow: false,
      aboutShow: false,
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
              eTitle: '1.IOST Official',
              content: [
                '安装谷歌插件钱包<a style="color: #418FF4;" target="_blank" href="https://chrome.google.com/webstore/detail/kncchdigobghenbbaddojjnnaogfppfj">iwallet</a>，并导入您的IOST账号。',
                '使用Chrome浏览器打开<a style="color: #418FF4;" target="_blank" href="https://www.iostabc.com/producers?page=1&size=50&sort_by=votes&order=desc">IOST官方投票</a>页面，为BlackPool投票。'
              ],
              eContent: [
                'Install <a style="color: #418FF4;" target="_blank" href="https://chrome.google.com/webstore/detail/kncchdigobghenbbaddojjnnaogfppfj">iwallet</a> and import your IOST account.',
                'Scan the <a style="color: #418FF4;" target="_blank" href="https://www.iostabc.com/producers?page=1&size=50&sort_by=votes&order=desc">IOST official voting</a> page and vote BlackPool.'
              ]
            },
            {
              title: '2.TokenPocket钱包投票',
              eTitle: '2.TokenPocket',
              content: [
                '下载<a style="color: #418FF4;" target="_blank" href="https://www.tokenpocket.pro/">TokenPocket</a>钱包，注册IOST钱包。',
                '在资产页面，点击投票，搜索BlackPool，输入投票数并确认投票成功。',
                '在该页面可以领取每日奖励和季度奖励。'
              ],
              eContent: [
                'Download <a style="color: #418FF4;" target="_blank" href="https://www.tokenpocket.pro/">TokenPocket</a> and add IOST account.',
                'Click Vote in Assets page and search BlackPool, confirm your vote.',
                'Get your bonus in this page.'
              ]
            },
            {
              title: '3.Biss交易所投票',
              eTitle: '3.Biss',
              content: [
                '打开<a style="color: #418FF4;" target="_blank" href="https://iost.biss.com/#/vote">Biss交易所投票</a>页面。',
                '在搜索栏搜索BlackPool，并点击投票。'
              ],
              eContent: [
                'Scan the <a style="color: #418FF4;" target="_blank" href="https://iost.biss.com/#/vote">Biss voting page</a>.',
                'Search BlackPool and vote.'
              ]
            }
          ],
          prompt:''
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
              title: '1.使用Chrome安装 <a style="color: #418FF4;" target="_blank" href="https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn">MetaMask</a>，导入存放了IOTX的钱包，钱包中需要有少量ETH支付投票过程中的gas费用',
              eTitle: '1.Install <a style="color: #418FF4;" target="_blank" href="https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn">MetaMask</a>, import your account and add IOTX token',
              content: '',
              eContent: ''
            },
            {
              title: '2.前往<a style="color: #418FF4;" target="_blank" href="https://member.iotex.io/delegate/5ce3db613324884dffa7772d">IOTEX官方投票</a>，页面，输入所投IOTX数量，选择投票时长获取额外票数，建议开启自动质押，填好信息后确认投票',
              eTitle: '2.Scan the <a style="color: #418FF4;" target="_blank" href="https://member.iotex.io/delegate/5ce3db613324884dffa7772d">IoTeX official voting page</a> and filled the form, confirm the vote information and vote',
              content: '',
              eContent: ''
            },
            {
              title: '3.在MetaMask确认两笔交易，两笔交易均成功后则投票成功',
              eTitle: '3.Confirm 2 transactions on Metamask, your vote will succeed when transactions finished',
              content: '',
              eContent: ''
            }
          ],
          prompt:''
        },
        {
          icon: decred,
          name: 'Chainx',
          btnText: '委托',
          btnEnglishText: 'Coming',
          value: '24%-80%',
          state: true,
          text: [
            {
              title: '1.访问<a style="color: #418FF4;" target="_blank" href="https://wallet.chainx.org/">ChainX 钱包</a>，注册或导入账户',
              eTitle: '1.Visit <a style="color: #418FF4;" target="_blank" href="https://wallet.chainx.org/">ChainX Wallet</a>,create or import an account',
              content: ''
            },
            {
              title: '2.在<a style="color: #418FF4;" target="_blank" href="https://wallet.chainx.org/election">投票选举页面</a>为BlackPool投票',
              eTitle: '2.Vote BlackPool on the <a style="color: #418FF4;" target="_blank" href="https://wallet.chainx.org/election">vote page</a>',
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
              title: '1.在Chrome浏览器使用<a style="color: #418FF4;" target="_blank" href="https://get-scatter.com/download">Scatter</a>登陆<a style="color: #418FF4;" target="_blank" href="https://bos.eosx.io/tools/vote">官方投票网站</a>',
              eTitle: '1.Log in Chrome with <a style="color: #418FF4;" target="_blank" href="https://get-scatter.com/download">Scatter</a> and scan the <a style="color: #418FF4;" target="_blank" href="https://bos.eosx.io/tools/vote">BOS official voting page</a>',
              content: ''
            },
            {
              title: '2.节点账号搜索BlackPool',
              eTitle: '2.Search BlackPool',
              content: ''
            },
            {
              title: '3.勾选BlackPool名字前的方块，点击投票',
              eTitle: '3.Select BlackPool and vote',
              content: ''
            }
          ],
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
      let clock
      if(clock){
        clearTimeout(clock)
       
      }
      clock=setTimeout(()=>{
        //blackpool监听滚动
        let scrollTop = document.documentElement.scrollTop? document.documentElement.scrollTop:window.pageYOffset 
        let windowHeight = window.innerHeight 
        let blackpoolTop=this.$refs.card.offsetTop+200
        if(blackpoolTop<windowHeight+scrollTop){
          this.blackpoolShow = true
        } else {
          this.blackpoolShow = false
        }
        //优势部分滚动监听
        let superiorityTop=this.$refs.superiority.offsetTop+200
        if(superiorityTop<windowHeight+scrollTop){
          this.cardShow = true
        } else {
          this.cardShow = false
        }
        // 关于部分滚动监听
        let aboutTop=this.$refs.aboutDom.offsetTop+200
        if(aboutTop<windowHeight+scrollTop){
          this.aboutShow = true
        } else {
          this.aboutShow = false
        }
      },300);
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
@media screen and (min-width: 10px) and (max-width: 500px){
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
        width: 110px;
        margin: 13px 0;
        height: 30px;
        background-image: url("../assets/logo.png");
        // background-position: center;
        // background-size:contain;
        background-repeat: no-repeat;
        float: left;
      }
    }
    .nav-button {
      padding-right:10px;
      font-size: 12px;
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
          padding-right: 4px;
        }
        .sign-up {
          padding-left: 4px;
        }
        .en {
          padding-left: 20px;
        }
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
    // min-width: 1120px;
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
@media screen and (min-width: 10px) and (max-width: 1120px){
  #home {
    margin-top: 56px;
    height: auto;
    background-image: url("../assets/image/bg.png");
    background-position: center;
    background-size:10px;
    // background-repeat: no-repeat;
    .layout {
      margin: 0 auto;
      max-width: 1200px;
      // min-width: 1120px;
      box-sizing: border-box;
      padding: 20px 0px;
      text-align: center;
    }
    .intro-img {
      float: inherit;
      margin: 0  auto;
      width: 250px;
      height: 250px;
      padding-top: 0;
      // background-color: pink;
      background-image: url("../assets/image/el.png");
      background-position: center;
      background-size:contain;
      background-repeat: no-repeat;
    }
    .intro-text {
      float: inherit;
      margin: 40px 0;
      text-align: center;
      h1 {
        font-size: 32px;
        color: #1B1B1B;
        letter-spacing: 2.26px;
        font-weight:700;
      }
      h2 {
        // font-family: ArialMT;
        font-size: 16px;
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
    .blackpool-min-h {
      min-height: 634px;
    }
    .card-min-h {
      min-height: 368px;
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
    min-height: 413px;
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
@media screen and (min-width: 10px) and (max-width: 950px){
  .about {
    background-color: #F6FCFF;
    .layout {
      margin: 0 auto;
      max-width: 1200px;
      min-height: 413px;
      // min-width: 1120px;
      box-sizing: border-box;
      padding: 100px 0;
      text-align: center;
      .icon {
        float: inherit;
        width: 300px;
        margin-left: 0;
      }
      .about-text {
        text-align: center;
        margin: 60px 30px 20px 30px;
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
      a {
        position: relative;
        .logo {
          margin: 0 40px;
        }
        .qrcode {
          position: absolute;
          top: 160%;
          left: 50%;
          z-index: 100;
          padding: 10px;
          background-color: #fff;
          margin-left: -110px;
          box-shadow: 0 0 10px 0 rgba(195,195,195,0.50);
          opacity: 0;
          transition: all .6s ease;
        }
        .wx-logo:hover+.qrcode{
          opacity: 1;
        }
        .logo:hover {
          transition: all .6s ease;
          transform:scale(1.5)
        }
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

.card1-enter-active, .card1-leave-active {
  transition: all .6s ease;
}
.card1-enter, .card1-leave-to {
  opacity: 0;
  transform: translateY(70px);
}

.card2-enter-active, .card2-leave-active {
  transition: all .6s ease;
  transition-delay: .3s;
}
.card2-enter, .card2-leave-to {
  opacity: 0;
  transform: translateY(70px);
}

.card3-enter-active, .card3-leave-active {
  transition: all .6s ease;
  transition-delay: .6s;
}
.card3-enter, .card3-leave-to {
  opacity: 0;
  transform: translateY(70px);
}

.card4-enter-active, .card4-leave-active {
  transition: all .6s ease;
  transition-delay: .9s;
}
.card4-enter, .card4-leave-to {
  opacity: 0;
  transform: translateY(70px);
}

.about-left-enter-active, .about-left-leave-active {
  transition: all 1s ease;
}
.about-left-enter, .about-left-leave-to {
  opacity: 0;
  transform: translateX(-70px);
}

.about-right-enter-active, .about-right-leave-active {
  transition: all 1s ease;
}
.about-right-enter, .about-right-leave-to {
  opacity: 0;
  transform: translateX(70px);
}
</style>
