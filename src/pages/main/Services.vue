<template>

  <!-- <div
    class="fit transparent text-justify row wrap justify-center items-start"
  > -->
  <div class="transparent q-pt-xl">
    <!-- <div class="transparent q-pa-md text-justify row wrap justify-center items-start content-start"> -->
      <!-- <div class="q-pa-md col-xs-12 col-sm-6 col-md-4" style="max-width:415px"> -->
        <!-- 3d animation using pure CSS3 -->
    <!-- <h1><small>Movie Posters Example</small></h1> -->
      <h1 class="text-center">
        <small><strong> Criando um</strong><strong style="color: #620fef;"> único</strong><strong> produto,</strong>
        <br>
        <strong> presente em todas as</strong><strong style="color: #620fef;"> plataformas.</strong></small>
      </h1>
      <div id="perspective3d" class="transparent text-justify row wrap justify-center items-start content-start">
        <transition name="bounce" mode="out-in">
        <div v-if="firstCard" class="card row q-pa-md col-xs-12 col-sm-12 col-md-12">
          <div id="mac2-preview" class="platform-mac mat-only">
          </div>
        </div>
        </transition>
        <div class="card row q-pa-md col-xs-12 col-sm-12 col-md-6">
        <div class="col">
          <div id="mac2-preview" class="platform-mac mat-only">
            <!-- <iframe id="mac2-iframe" frameborder="0" :src="'http://localhost:8080/#' + this.$route.fullPath"/> -->
          </div>
        </div>
        </div>
        <div class="card row q-pa-md col-xs-12 col-sm-12 col-md-6">
        <div class="col">
          <div id="mac3-preview" class="platform-mac mat-only">
          </div>
        </div>
        </div>
        <div class="q-pa-md col-xs-12 col-sm-12 col-md-6">
        <div id="mac2-preview" class="platform-mac mat-only">
          <iframe id="mac2-iframe" frameborder="0" :src="'http://localhost:8080/#' + this.$route.fullPath"/>
        </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // crep: false
      firstCard: true
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll (event) {
      if (window.scrollY > 290) {
        this.firstCard = false
      } else if (window.scrollY === 0) {
        this.firstCard = true
      }
    }
  }
}
</script>

<style scoped>
#perspective3d .card #mac2-preview {
  border:1px solid #fff;
  -webkit-transform: rotateY(10deg);
  -moz-box-shadow:0 3px 10px #888;
  -webkit-box-shadow:0 3px 10px #888;
  -webkit-transition-property: transform;
  -webkit-transition-duration: 1s;
  /* margin: 0 0 18vw 0; */
}
#perspective3d .card:hover #mac2-preview {
  -webkit-transform: rotateY(0deg);
  /* margin: 0 auto 0; */
}

#mac2-preview {
  text-align: center;
  /* align-items: center; */
  /* width: 93vw; */

  height: 700px;
  background: url('../../assets/logo/your-design-trans-light.png') center center no-repeat;
  background-size: 1000px;
  /* margin: -25px auto 0; */
}

#perspective3d .card #mac3-preview {
  border:1px solid #fff;
  -webkit-transform: rotateY(-10deg);
  -moz-box-shadow:0 3px 10px #888;
  -webkit-box-shadow:0 3px 10px #888;
  -webkit-transition-property: transform;
  -webkit-transition-duration: 1s;
  /* margin: 0 0 18vw 0; */
}
#perspective3d .card:hover #mac3-preview {
  -webkit-transform: rotateY(0deg);
  /* margin: 0 auto 0; */
}

#mac3-preview {
  text-align: center;
  /* align-items: center; */
  /* width: 93vw; */

  height: 700px;
  background: url('../../assets/logo/your-design-trans.png') center center no-repeat;
  background-size: 1000px;
  /* margin: -25px auto 0; */
}

/* #mac2-preview iframe {
  position: absolute;
  margin: 94px -323px 0;
  width: 644px;
  height: 364px;
} */

/* BASIC RESET */
ul,ol,li,.card,h1,h2,h3,h4,h5,h6,pre,form,body,html,p,blockquote,fieldset,input{margin:0; padding:0;}

/* HTML ELEMENTS */
/* body { background-color:#deddcd; font:14px/21px Arial,Helvetica,sans-serif; } */
h1 { font: bold 65px/60px Helvetica, Arial, Sans-serif; text-shadow: 0px 8px 14px #333; }
h1 small{ font-size: 20px; text-transform:uppercase; letter-spacing: 14px; display: block; }
/* h2 a { display: block; text-decoration: none; margin: 0 0 30px 0; font: italic 45px Georgia, Times, Serif;  text-align: center; color: #bfe1f1; text-shadow: 0px 2px 6px #333; }
h2 a:hover { color: #90bcd0; } */

/* COMMON CLASSES */
.break {
  clear:both;
}

/* WRAPPER */
#wrapper {
  width:960px;
  margin:40px auto;
}

/* CONTENT */
#content { }
#content .info {
  padding:10px;
}

/* MOVIE POSTERS */
#perspective3d {
  justify: center;
  list-style:none;
  margin:0 0;
  height:550px;
}
#perspective3d .card {
  margin:100px 0;
  display:inline;
  float:left;
  -webkit-perspective: 500;
  -webkit-transform-style: preserve-3d;
  -webkit-transition-property: perspective;
  -webkit-transition-duration: 0.5s;
}

#perspective3d .card:hover {
  /* -webkit-perspective: 5000; */
}

/* #perspective3d li img {
  border:10px solid #fcfafa;
  -webkit-transform: rotateY(30deg);
  -moz-box-shadow:0 3px 10px #888;
  -webkit-box-shadow:0 3px 10px #888;
  -webkit-transition-property: transform;
  -webkit-transition-duration: 0.5s;
}
#perspective3d li:hover img {
  -webkit-transform: rotateY(0deg);
} */

/* .movieinfo {
  border:10px solid #fcfafa;
  padding:20px; width:200px;
  height:180px;
  background-color:#deddcd;
  margin:-195px 0 0 55px;
  position:absolute;
  -moz-box-shadow:0 20px 40px #888;
  -webkit-box-shadow:0 20px 40px #888;
  -webkit-transform: translateZ(30px)
  rotateY(30deg);
  -webkit-transition-property: transform, box-shadow, margin;
  -webkit-transition-duration: 0.5s;
}
#perspective3d li:hover .movieinfo {
  -webkit-transform: rotateY(0deg);
  -webkit-box-shadow:0 5px 10px #888;
  margin:-175px 0 0 30px;
}
.movieinfo h3 {
  color:#7a3f3a;
  font-variant: small-caps;
  font-family:Georgia,serif,Times;
  text-align:center;
  padding-bottom:15px;
}
.movieinfo p {
  padding-bottom:15px;
}
.movieinfo a {
  background-color:#7a3f3a;
  padding:5px 10px;
  color:#eee;
  text-decoration:none;
  display:block;
  width:80px;
  text-align:center;
  margin:0 auto;
  -moz-border-radius:5px;
  -webkit-border-radius:5px;
}
.movieinfo a:hover, .movieinfo a:focus {
  background-color:#6a191f;
  color:#fff;
} */
</style>
