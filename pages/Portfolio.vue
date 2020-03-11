<template>
    <div>
      <gnbs></gnbs>
      
      <div id="project">
			<h2 class="title">Portfolio</h2>	
	
			<div class="content">
				<ul id="proj_list" class="project_list">

					<li class="list" v-for='(port, index) in portList' :key='index' :class='{shadow : port.img}' @click='flip(index)'>
						<div v-if="port.img">
							<div class="thum">
								<img :src='port.img'/>
								<div class="gradient top">
									<p class="front-title">{{ port.project }}</p>
									<p class="front-sub">{{ port.option + " by " + port.date }}</p>
								</div>
								<div class="gradient bottom"></div>
							</div>
							<div class="txt_area">
								<p class="date txt">{{port.date}}</p>
								<p class="pro txt">{{ port.project }}</p>
								<p class="op txt">- {{port.option}} 프로젝트</p>
								<p class="op txt" v-for='(scription, index) in port.scription' :key='index'>- {{scription}}</p>
								<a :href='port.alink' class="btn_link" v-if='port.alink !== "#"'>- {{port.alink}}</a>
								<div class="skill">
									<img v-for='(skill, index) in port.skill' :key='index' :src='"img/logo/" + skill + ".png"' :alt='skill' >
								</div>
							</div>
						</div>
					</li>

				</ul>
			</div>
		</div>
    </div>
</template>

<script>
import Gnbs from './inc/Gnb.vue'

export default {
  name : "Portfolio",
  components : {
    Gnbs
  },
  data () {
    return {
	  isActive : "active",
	  show: false,
	  layerData: null,
	  portList : [
		  {img : 'img/26_s.jpg', project : '덕후생활', option: "sns 앱", scription: ["react native / redux를 사용해 UI / 데이터 연동", "jira / bitbuket으로 이슈 / 소스관리"], date : '2019-05 ~ ', alink : '#', skill: ["react", "redux"]},
		  {img : 'img/25_s.jpg', project : 'OBIDO', option: "네비게이션 웹앱", scription: ["vue / vuex / scss를 사용해 UI / 데이터 연동", "github으로 소스관리"], date : '2019-11 ~ 2020-01', alink : '#', skill: ["vue", "scss"]},
		  {img : 'img/24_s.jpg', project : 'KwaveStar', option: "한류 타겟 웹 / 모바일 반응형", scription: ["mediaQuery로 반응형 웹 작업", "모바일앱 react native UI 작업", "jira / bitbuket으로 이슈 / 소스관리"], date : '2018-10 ~ ', alink : 'http://kr.kwavestar.com/', skill: ["html", "css", "js", "jquery", "react", "scss"]},
		  {img : 'img/23_s.jpg', project : 'SPC', option: "디지털 사이니지", scription: ["vue / scss를 사용해 UI 작업", "git으로 소스관리"], date : '2017-07 ~ 2018-09', alink : '#', skill: ["vue", "scss"]},
		  {img : 'img/22_s.jpg', project : 'LG전자', option: "LG전자 반응형", scription: ["IE7 크로스브라우징", "mediaQuery로 반응형 웹 작업"], date : '2016-08 ~ 2017-03', alink : 'http://www.lge.co.kr/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/21_s.jpg', project : '판도라티비', option: "동영상미디어 웹 / 모바일 반응형", scription: ["IE6 크로스브라우징", "mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2013-05 ~ 2016-07', alink : 'http://www.pandora.tv/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/20_s.jpg', project : '코리아탑백', option: "한류 동영상미디어 웹 / 모바일 반응형", scription: ["mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2016-03 ~ 2016-07', alink : 'http://100.pandora.tv/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/19_s.jpg', project : '그리드인코딩', option: "인코딩 솔루션 웹", scription: ["데이터 연동", "mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2015-10 ~ 2016-02', alink : 'http://www.gridencoding.com/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/18_s.jpg', project : '아이앱', option: "1인 모바일 미디어 웹 / 모바일 반응형", scription: ["mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2014-05 ~ 2015-02', alink : '#', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/17_s.jpg', project : 'KMPlayer', option: "웹 / 플레이어 웹뷰", scription: ["IE5 크로스브라우징", "mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2013-05 ~ 2016-07', alink : 'http://www.kmplayer.com/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/16_s.jpg', project : '판도라 게임 TV', option: "웹 / 모바일 반응형", scription: ["mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2013-10 ~ 2013-12', alink : 'http://game.pandora.tv/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/15_s.jpg', project : '젤리팟', option: "팟캐스트 웹 / 모바일 반응형", scription: ["mediaQuery로 반응형 웹 작업", "redmine로 이슈관리"], date : '2013-06 ~ 2013-10', alink : 'http://www.jellypod.com/', skill: ["html", "css", "js", "jquery"]},
		//   {img : 'img/14_s.jpg', project : '에브리온 TV', option: "", scription: [], date : '', alink : 'http://www.everyon.tv/', skill: []},
		//   {img : 'img/13_s.jpg', project : '젤리캠', option: "", scription: [], date : '', alink : 'http://www.jellycam.com/', skill: []},
		  {img : 'img/12_s.png', project : '신한카드', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2013-02 ~ 2013-04', alink : 'http://www.shinhancard.com/', skill: ["html", "css", "js", "jquery"]},
		//   {img : 'img/11_s.jpg', project : '미디어크리에이트', option: "웹표준", scription: [], date : '2012-12 ~ 2013-01', alink : 'http://www.mediacreate.co.kr/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/10_s.png', project : '삼성카드', option: "사회공헌 웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '', alink : 'http://www.samsungcard.com/csr/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/09_s.jpg', project : 'Cj채용', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2012-11 ~ 2013-12', alink : 'http://recruit.cj.net/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/08_s.jpg', project : '롯데리조트', option: "웹표준", scription: [], date : '2012-07 ~ 2012-08', alink : 'http://www.lottejejuresort.com/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/07_s.jpg', project : 'T world shop', option: "쇼핑몰 웹표준", scription: ["IE6 크로스브라우징"], date : '2012-05 ~ 2012-06', alink : 'http://www.tworldshop.co.kr/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/06_s.jpg', project : '오케이아웃도어', option: "쇼핑몰 웹표준", scription: ["IE6 크로스브라우징"], date : '2012-01 ~ 2012-05', alink : 'http://www.okoutdoor.com/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/05_s.jpg', project : '대우증권', option: "사내 모바일앱", scription: ["하이브리드 웹앱"], date : '2011-09 ~ 2011-12', alink : '#', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/04_s.jpg', project : '교육학술정보원', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2011-06 ~ 2011-08', alink : 'http://www.keris.or.kr/', skill: ["html", "css", "js", "jquery"]},
		  {img : 'img/03_s.jpg', project : '금융감독원', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2010-12 ~ 2011-03', alink : 'http://www.fss.or.kr/', skill: ["html", "css", "js"]},
		  {img : 'img/02_s.jpg', project : '조달청', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2010-09 ~ 2010-11', alink : 'http://www.pps.go.kr/', skill: ["html", "css", "js"]},
		  {img : 'img/01_s.jpg', project : '국립공원관리공단', option: "웹표준 / 웹접근성", scription: ["IE6 크로스브라우징", "웹접근성 마크 획득"], date : '2010-06 ~ 2010-08', alink : 'http://www.knps.or.kr/', skill: ["html", "css", "js"]}
	  ]
    }
  },
  mounted () {
	const listLeng = this.portList.length % 4
	const empty = {img : '', project : '', option: "", scription: [], date : '', alink : '', skill: []}
	document.querySelector('.gnb_area').childNodes[1].className = this.isActive

	for(let i = 0; listLeng > i; i++){
    	this.portList.push(empty)
	}
		
  },
  methods: {
	flip: (idx) => {
		const list = document.querySelectorAll('.list');
        for(let i = 0; list.length>i; i++){
			list[i].childNodes[0].className = ""
		}
		list[idx].childNodes[0].className = "flip"
	}
  } 
}
</script>

<style>
#project{width:100%;margin:0 auto;}
.project_list { overflow:hidden;display: flex;flex-wrap: wrap; align-items: center;justify-content: center;}
.project_list .list { float:left; width:270px;height:300px; margin:7px; position: relative;overflow: hidden;perspective: 1000;border-radius: 14px;}
.shadow{box-shadow: 0 1px 4px 0 rgba(225, 225, 225, .5);}
.project_list .list > div{width:100%;height:100%;transition:all 1s ease;transform-style: preserve-3d;perspective: 1000;}
.project_list .list .thum, .project_list .list .txt_area{width:100%;height:100%;position:absolute;left:0;top:0;backface-visibility: hidden;}
.project_list .list .thum{transform: rotateY(0);-moz-transform: rotateY(0);-ms-transform: rotateY(0);-webkit-transform: rotateY(0);}
.project_list .list .thum img {width:100%;height:100%;position:absolute;left:50%;top:50%;transform: translate(-50%, -50%);}
.project_list .list .thum .gradient{width: 100%;height: 30%;position: absolute;left: 0;}
.project_list .list .thum .gradient.top{background: linear-gradient(rgba(0, 0, 0, 0.4),rgba(0, 0, 0, 0));top: 0;}
.project_list .list .thum .gradient.bottom{background: linear-gradient(rgb(225, 225, 225, 0),rgba(225, 225, 225, 0.3));bottom: 0;}
.project_list .list .thum .gradient .front-title{font-size: 18px;color: #fff;margin: 15px 0 0 20px;font-family: 'gothic';}
.project_list .list .thum .gradient .front-sub{font-size: 12px;color: #fff;margin: 1px 0 0 20px;font-family: 'gothic';}
.project_list .list .txt_area{
display: flex;flex-direction: column;background: #fff;position: relative;
transform: rotateY(180deg);-moz-transform: rotateY(180deg);-ms-transform: rotateY(180deg);-webkit-transform: rotateY(180deg);
}
.project_list .list .txt { color:#000;text-align:left; width: calc(100% - 30px);padding:0 15px;}
.project_list .list .txt.pro {font-size:20px;margin-bottom:5px;font-weight: bold;}
.project_list .list .txt.op {font-size:14px;opacity: .6;}
.project_list .list .txt.date {font-size:12px;opacity: .6;margin-top:40px;}
.project_list .list .skill{position: absolute;right: 15px;bottom: 20px;}
.project_list .list .skill img{height: 30px;margin: 0 3px;}
.project_list .list:hover > div{ transform: rotateY(180deg);-moz-transform: rotateY(180deg);-ms-transform: rotateY(180deg);-webkit-transform: rotateY(180deg);}
.btn_link{
    display:block;
	width: calc(100% - 30px);padding:0 15px;
    font-size: 14px;
    color:rgba(0, 0, 0, 0.6);
	text-decoration: underline;
    /* background-color: #52d3aa;
    text-transform:uppercase;
    background-image: -webkit-gradient(linear, 0% 0%, 100% 100%, color-stop(0, #3f95ea), color-stop(1, #52d3aa));
    background-image: -webkit-repeating-linear-gradient(top left, #3f95ea 0%, #52d3aa 100%);
    background-image: repeating-linear-gradient(to bottom right, #3f95ea 0%, #52d3aa 100%);
    background-image: -ms-repeating-linear-gradient(top left, #3f95ea 0%, #52d3aa 100%); */
    }

@media all and (max-width:768px) {
.project_list .list { width:80%;  -webkit-box-sizing:border-box;  box-sizing:border-box; border-right:0 !important}
.project_list .list:hover > div{ transform: rotateY(0);-moz-transform: rotateY(0);-ms-transform: rotateY(0);-webkit-transform: rotateY(0);}
.project_list .list > div.flip{transform: rotateY(180deg);-moz-transform: rotateY(180deg);-ms-transform: rotateY(180deg);-webkit-transform: rotateY(180deg);}
/* .project_list .list .thum {height: 150px;position: relative;} */
/* .project_list .list .thum img{height:225px;} */
/* .project_list .list .txt_area{opacity: 1;left: 0;position: static;margin-top:20px;} */
/* .project_list .list .txt { color:#fff; margin-bottom:10px;} */
/* .project_list .list .txt strong {font-size:16px;} */
/* .btn_link{width:90%;margin-top:10px} */
/* .project_list .list:hover .thum img{opacity:1;} */
}
</style>
