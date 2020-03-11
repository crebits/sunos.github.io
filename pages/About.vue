<template>
    <div>
        <gnbs></gnbs>
        
        <div id="profile">
        <h2 class="title">About Me</h2>	
    
        <div class="content">
          <ul class="profile-list">
            <li><strong>Name</strong><span>최선호</span></li>
            <li><strong>Birth</strong><span>1986.09.02</span></li>
            <li><strong>Phone</strong><span>010-6690-5674</span></li>
            <li><strong>E-mail</strong><span>crebits@naver.com</span></li>
            <li>
              <strong>Skill</strong>
              <!-- <span>HTML5, CSS3, JavaScript, JQuery, Responsive Web, Mobile, Photoshop, Illustrator </span> -->
              <img src="img/logo/html.png" alt="html">
              <img src="img/logo/css.png" alt="css">
              <img src="img/logo/js.png" alt="js">
              <img src="img/logo/jquery.png" alt="jquery">
              <img src="img/logo/react.png" alt="react">
              <img src="img/logo/redux.png" alt="redux">
              <img src="img/logo/vue.png" alt="vue">
              <img src="img/logo/scss.png" alt="sass">
              <img src="img/logo/git.png" alt="git">
              <img src="img/logo/github.png" alt="github">
            </li>
            <li><strong>Career</strong>
              <span>
                <span class="not-desc"><strong>이컴라인</strong> / 2010.06 ~ 2011.03</span><br>
                <span class="not-desc"><strong>시도우</strong> / 2011.06 ~ 2012.10</span><br>
                <span class="not-desc"><strong>비스톤스</strong> / 2012.11 ~ 2013.05</span><br>
                <span class="not-desc"><strong>판도라티비</strong> / 2013.05 ~ 2016.08</span><br>
                <span class="not-desc"><strong>리젠컴퍼니</strong> / 2016.08 ~ 2017.03</span><br>
                <span class="not-desc"><strong>커머스랩</strong> / 2017.07 ~ 2018.09</span><br>
                <strong>카이퍼랩</strong> / 2018.10 ~ 
              </span>
            </li>
          </ul>
        </div>
      </div>
    </div>
</template>

<script>
import Gnbs from './inc/Gnb.vue'

export default {
  name : "About",
  components : {
    Gnbs
  },
  data () {
    return {
      isActive : "active"
    }
  },
  mounted () {
    return document.querySelector('.gnb_area').childNodes[2].className = this.isActive
  }
}
</script>

<style>
#profile h2.title{margin-bottom: -15px;background: #000;display: inline-block;padding:20px;}
#profile .content{padding:30px 0 0;background-color: #000;border:1px solid #fff;border-left:none;border-top:none; box-shadow: #fff 5px 5px 5px;z-index:-1;transform: skewY(-5deg);-moz-transform: skewY(-5deg);-ms-transform: skewY(-5deg);-webkit-transform: skewY(-5deg);}
#profile .intro_area{width:100%;text-align:center;transform: skewY(7deg);-moz-transform: skewY(7deg);-ms-transform: skewY(7deg);-webkit-transform: skewY(7deg);}
#profile .intro_area h2{font-size: 62px;color: #999;text-shadow: 0 -3px 0px #fff;}
#profile .intro_area .sub{font-size: 28px;color: #999;font-weight: bold;text-shadow: 0 -2px 0px #fff;}
#profile .intro {font-size: 26px;color: #999;text-shadow: 0 -2px 0px #fff;}
.profile-list{margin: 0 auto;padding-bottom:50px;width: 80%;transform: skewY(5deg);-moz-transform: skewY(5deg);-ms-transform: skewY(5deg);-webkit-transform: skewY(5deg);}
.profile-list li{margin:10px 0 0 0;line-height: 30px;text-align:left;color: #fff;font-size: 20px;}
.profile-list li>strong{display:inline-block;width:80px;font-family:'Varela Round', sans-serif; vertical-align:top}
.profile-list li span{display:inline-block;}
.profile-list li .not-desc{text-decoration:line-through;color:#666;}
.profile-list li img{height:35px;margin-right: 10px;}

@media all and (max-width:768px) {
	#profile, #order{padding:50px 5% 0;}
  #profile .content{padding:10px 0 0;}
  #profile h2.title{margin-bottom:0;padding-left:0;}
	.profile-list{width:100%;}
	.profile-list li{font-size:18px;line-height:26px;}
}
</style>
