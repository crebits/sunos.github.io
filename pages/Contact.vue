<template>
    <div>
        <gnbs></gnbs>

        <div id="order">
			<h2 class="title">Contact</h2>	
	
			<div class="content">
				<dl class="con_list">
					<dt>Address</dt>
					<dd>South Korea, Gyeonggi-do, Seong-nam</dd>
					<dt>KaKaoTalk</dt>
					<dd>crebits</dd>
					<dt>TEL</dt>
					<dd><a href="tel:010-8783-7284">010-6690-5674</a></dd>
					<dt>E-mail</dt>
					<dd><a href="mailto:crebits@naver.com">crebits@naver.com</a></dd>
				</dl>
			</div>	
		</div>
    </div>    
</template>

<script>
import Gnbs from "./inc/Gnb.vue"

export default {
    name : 'contact',
    components : {
        Gnbs
    },
  data () {
    return {
      isActive : "active"
    }
  },
  mounted () {
    return document.querySelector('.gnb_area').childNodes[3].className = this.isActive
  }
}
</script>

<style>
#order .content{padding:0 0 50px;background:#fff;}
#order .info { margin-bottom:20px }
#order .inner_box { position:absolute; left:50%; margin-left:-300px; top:200px; width:600px;transform: skewY(7deg);-moz-transform: skewY(7deg);-ms-transform: skewY(7deg);-webkit-transform: skewY(7deg);}
#order .inp_box { float:left; margin-right:10px; margin-bottom:15px }
#order .form_box input[type="text"] { height:60px; line-height:60px; border-radius:7px; border:0; background:#fff; margin:0; padding:0 0 0 20px; font-size:16px;}
#order .form_box input[type="button"] { height:60px; line-height:60px; border-radius:7px; border:0; background:#4297d8; margin:0; padding:0; width:86px; text-align:center; color:#fff; font-weight:bold; cursor:pointer }
#order .form_box textarea { padding:20px; line-height:20px; font-size:16px; width:560px; height:110px; border-radius:7px; margin:0; border:0; font-family:Arial, Helvetica, sans-serif; }
.con_list{transform: skewY(7deg);-moz-transform: skewY(7deg);-ms-transform: skewY(7deg);-webkit-transform: skewY(7deg);transform-origin: 0 0;width: 80%;margin: 0 auto 70px;}
.con_list dt{width: 100%;font-size: 26px;font-weight: bold;text-transform: uppercase;color: #fff;letter-spacing: -1px;text-shadow: -1px -2px 0px #000;line-height: 26px;margin: 40px 0 15px;}
.con_list dd{color: #000;font-size: 26px;line-height: 46px;padding-bottom: 5px;border-bottom: 1px dotted #ccc;}
.con_list dd a{color:#000;}

.address{position: absolute;right: 30px;bottom: 35px;text-align: right;}
.address p{color:#fff;font-weight: bold;font-size: 13px;line-height: 18px;}
.address p.name{margin-right: 5px;}

@media all and (max-width:768px) {
	#order {padding-bottom:40px; }
	#order .content{padding:0;}
	.con_list{padding-top:10px;}
	.con_list dt{font-size: 20px;line-height: 21px;margin: 25px 0 10px;}
	.con_list dd{font-size: 18px;line-height: 26px;padding-bottom: 25px;}
	.address{right:5%;bottom:10px;}
}
</style>
