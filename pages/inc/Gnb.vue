<template>
    <transition class="gnb" name="test">
        <ul class="gnb_area">
            <li v-for='(list, index) in linklist' :key='index' v-on:click='gnbClick(index)'>
                <router-link :to='list.link'>{{ list.content }}</router-link>
            </li>
        </ul>
	</transition>
</template>

<script>
export default {
    name : "gnb",
    data () {
        return {
	          isActive : "active",
            linklist : [
                {content: 'HOME', link: '/'},
                {content: 'Portfolio', link: '/portfolio'},
                {content: 'About Me', link: '/about'},
                // {content: 'Contact', link: '/contact'}
            ],
            title: this.$route.name
        }
    },  
    transition: {
        name: 'test',
        mode: 'out-in'
    },
    methods: {
      gnbClick: function(idx){
         var gnb = document.querySelector('.gnb_area');
         for(let i = 0; gnb.childNodes.length>i; i++){
           gnb.childNodes[i].className = ""
         }
         
         gnb.childNodes[idx].className = this.isActive
      }
    }
}
</script>

<style>
.gnb_area { width:100%; position:fixed; left:0; top:0; background:rgba(0,0,0,0.6);z-index:999999;text-align:center;padding:10px 0;}
.gnb_area li{display:inline-block;position:relative;}
.gnb_area li a { display:block;padding:10px 30px;color:#fff;font-size:16px;}
.gnb_area li a:before {content:'';position:absolute;bottom:0;left:0;width:100%;height:0;background:#fff;-webkit-transition:-webkit-transform 0.7s;transition:transform 0.7s;-webkit-transform:scale3d(0, 1, 1);transform: scale3d(0, 1, 1);}
.gnb_area li.active a:before {-webkit-transform: scale3d(1, 1, 1);transform:scale3d(1, 1, 1);height:1px;}

@media all and (max-width:768px) {
	.gnb_area li { width:25%; text-align:center; line-height:30px; }
	.gnb_area li a {padding:0}
}
.page-enter-active {
  animation: bounce-in .5s;
}
.page-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>
