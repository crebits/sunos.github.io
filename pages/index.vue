<template>
  <section class="container">
    <gnbs></gnbs>    
		<div class="home">
			<h1 class="sunos" ref="logo">Suno's</h1>
		</div>
  </section>
</template>

<script>
import Gnbs from './inc/Gnb.vue'

export default {
  components: {
    Gnbs
  },
  data () {
    return {
      isActive: 'active'
    }
  },
  mounted () {
    return document.querySelector('.gnb_area').childNodes[0].className = this.isActive
  }
}
</script>

<style>
@keyframes title {
    0%   {top:-1000px ;opacity:0;}
    50%  {top:50%;opacity:0;}
    60%  {opacity:1;}
    80%  {top:38%;}
    100% {top:50%;}
}
/* .home{padding:350px 0;} */
html, body{height:100%;}
h1.sunos{width:100%;animation-name: title;animation-duration:1.3s;font-family: 'Kaushan Script', sans-serif;font-size: 100px;text-align: center;color: #fff;line-height: 101px;position: absolute;top: 50%;transform: translate(0, -50%);}
#__nuxt, #__layout, #__layout>div, .container{height:100%;}
@media all and (max-width:768px) {	
	#home{padding:70px 0 45px;}
	h1.sunos{font-size:50px;line-height:51px;}
}
</style>
