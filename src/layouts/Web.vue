<template>
<div>
    <q-layout
      view="lHr LpR fff"
      style="background-image: linear-gradient(to bottom right, white, black);"
    >
      <!-- :style="'background-color: ' + $store.state.colors.themeBGColor + '; color: ' + $store.state.colors.themeColor" -->
        <!-- class="transparent" -->
      <q-header
      reveal
        :style="$store.state.colors.themeBGColor != '' ?
          'background-color: ' + $store.state.colors.themeBGColor + '; color: ' + $store.state.colors.themeColor
          : $q.dark.isActive ? 'background-color: ' + $store.state.colors.darkThemeBGColor + '; color: ' + $store.state.colors.darkThemeColor
            : 'background-color: ' + $store.state.colors.lightThemeBGColor + '; color: ' + $store.state.colors.lightThemeColor"
      >
        <q-toolbar
        v-if="!headerTransitionVal"
          class="column q-pa-none"
          :class="headerTransition ? 'shadow-4' : ''"
        >
          <!-- :style="$q.dark.isActive ?
            'background-color: ' + darkThemeBGColor + '; color: ' + darkThemeColor
            : 'background-color: ' + lightThemeBGColor + '; color: ' + lightThemeColor" -->
        <div class="fit row wrap justify-end items-start content-start">
          <!-- <q-btn
            @click="left = !left"
            dense
            flat
            icon="menu"
            class="q-ml-xl q-mt-xl"
          /> -->
          <q-space v-if="$store.state.window.windowWidth <= 560"/>
          <div
            @click="$q.dark.toggle()"
            flat
            dense
            class="q-px-xl q-pt-xl"
          >
            <img class="footer-logo" :src="$q.dark.isActive ? require('../assets/logo/your-design-trans-white.png') : require('../assets/logo/your-design-trans.png')">
          </div>
          <q-space/>
          <!-- <q-btn
            @click="right = !right"
            dense

            flat
            icon="menu"
            class="q-mr-xl q-mt-xl"
          /> -->
          </div>
        <div class="fit row wrap justify-end items-start content-start">
          <q-space />
          <q-tabs :class="$store.state.window.windowWidth <= 560 ? '' : 'q-mr-xl'">
            <div @click="headerTab">
              <q-route-tab name="home" label="Início" to="/" class="q-pa-sm q-mt-xl"/>
            </div>
            <div @click="headerTab">
              <q-route-tab name="about" label="Sobre" to="/about" class="q-pa-sm q-mt-xl"/>
            </div>
            <div @click="headerTab">
              <q-route-tab name="services" label="Serviços" to="/services" class="q-pa-sm q-mt-xl"/>
            </div>
            <div @click="headerTab">
              <q-route-tab name="doubts" label="Dúvidas" to="/doubts" class="q-pa-sm q-mt-xl"/>
            </div>
          </q-tabs>
          <q-space v-if="$store.state.window.windowWidth <= 560"/>
        </div>
        </q-toolbar>
        <q-toolbar
          v-if="headerTransitionVal2"
          class="column"
          :class="headerTransition ? 'shadow-4' : ''"
          :style="$q.dark.isActive ?
            'background-color: ' + darkThemeBGColor + '; color: ' + darkThemeColor
            : 'background-color: ' + lightThemeBGColor + '; color: ' + lightThemeColor"
        >
        <div class="fit row wrap justify-end items-start content-start">
          <q-btn
            @click="left = !left"
            dense
            flat
            icon="menu"
            class="q-mt-sm"
          />
          <div
            @click="$q.dark.toggle()"
            flat
            dense
            class="q-pt-sm q-pl-sm"
          >
            <img class="footer-logo" :src="$q.dark.isActive ? require('../assets/logo/your-design-trans-white.png') : require('../assets/logo/your-design-trans.png')">
          </div>
          <q-space/>
          <q-btn
            v-if="$store.state.window.windowWidth <= 560"
            @click="right = !right"
            dense
            flat
            icon="menu"
            class="q-mt-sm q-ml-md"
          />
          <q-tabs class="q-ma-none">
            <div @click="headerTab">
              <q-route-tab name="home" label="Início" to="/" />
            </div>
            <div @click="headerTab">
              <q-route-tab name="about" label="Sobre" to="/about" />
            </div>
            <div @click="headerTab">
              <q-route-tab name="services" label="Serviços" to="/services" />
            </div>
            <div @click="headerTab">
              <q-route-tab name="doubts" label="Dúvidas" to="/doubts" />
            </div>
          </q-tabs>
          <q-btn
            v-if="$store.state.window.windowWidth > 560"
            @click="right = !right"
            dense
            flat
            icon="menu"
            class="q-mt-sm q-ml-md"
          />
          </div>
        </q-toolbar>
      <q-separator inset />
      </q-header>
      <q-drawer flat content-class="" bordered :width="250" v-model="left" side="left">
         <!-- <q-color no-header default-view="palette" :palette="palette" v-model="lightThemeBGColor" />
         <q-color no-header default-view="palette" :palette="palette" v-model="lightThemeColor" />
         <q-color no-header default-view="palette" :palette="palette" v-model="darkThemeBGColor" />
         <q-color no-header default-view="palette" :palette="palette" v-model="darkThemeColor" /> -->
        <LeftDrawer />
      </q-drawer>
      <q-drawer content-class="" bordered mini :width="65" v-model="right" side="right">
        <RightDrawer />
      </q-drawer>
      <q-page-container>
        <!-- {{ tabVal }} -->
        <!-- <FadeTransition/> -->
        <!-- <div v-if="this.$route.fullPath != '/'"
          class="q-px-xl fit row wrap justify-center items-start content-center"
          :class="this.$route.fullPath.search(/\bios\b/) >= 0 ? '' : ''"
        >
          <div
            class="q-pt-xs col-auto text-center">
            <q-tabs dense
              class="" no-caps>
              <q-tab
                icon="mdi-web"
                label="Web"
                @click="dynamicRoute('')"
              />
              <q-tab
                icon="mdi-apple-ios"
                label="iPhone"
                @click="dynamicRoute('/ios')"
              />
              <q-tab
                icon="mdi-google-play"
                label="Android" @click="dynamicRoute('/android')"
              />
              <q-tab
                icon="mdi-apple"
                label="Mac"
                @click="dynamicRoute('/mac')"
              />
              <q-tab
                icon="mdi-microsoft"
                label="Windows"
                @click="dynamicRoute('/windows')"
              />
            </q-tabs>
          </div>
        </div>
      <div v-else
        class="q-pa-xl fit row wrap justify-center items-start content-center"
        :class="this.$route.fullPath.search(/\bios\b/) >= 0 ? '' : ''"
      >
        <div class="col-auto text-center">
          <img class="footer-logo" :src="require('../assets/your-design-trans-light.png')">
            <div class="text-subtitle1"><strong>Criando um </strong><strong style="color: #a587ff;">único</strong>
              <strong> produto, presente em todas as </strong><strong style="color: #a587ff;">plataformas.</strong></div>
              <br>
              <div class="text-weight-bolder text-h6">
                Celulares / Tablets - iOS / Android
              </div>
              <div class="q-pb-none text-weight-bolder text-h6">
                Computadores / Web - MacOS X / Windows
              </div>
              <q-tabs no-caps>
                <q-route-tab icon="mdi-web" label="Web" to="/" />
                <q-route-tab icon="mdi-apple-ios" label="iPhone" to="/ios" />
                <q-route-tab icon="mdi-google-play" label="Android" to="/android" />
                <q-route-tab icon="mdi-apple" label="Mac" to="/mac" />
                <q-route-tab icon="mdi-microsoft" label="Windows" to="/windows" />
              </q-tabs>
              <DynamicCard/>
            <div>
          </div>
        </div>
      </div> -->
       <!-- <FadeTransition mode="out-in"> -->
         <!-- <div transition-show="jump-down"
  transition-hide="jump-up"> -->
   <!-- {{ tabVal }} -->
      <transition name="fade" mode="out-in">
        <router-view />
      </transition>
         <!-- </div> -->

       <!-- </FadeTransition> -->
      <whatsapp/>
      </q-page-container>
      <q-footer
      >
        <!-- reveal -->
        <!-- container
        style="height: 250px" -->
        <!-- :style="$q.dark.isActive ?
          'background-color: ' + lightThemeBGColor + '; color: ' + lightThemeColor :
          'background-color: ' + darkThemeBGColor + '; color: ' + darkThemeColor" -->
        <!-- <q-toolbar class="q-pa-lg"> -->
          <img class="footer-logo" :src="require('../assets/logo/your-design-trans.png')">
          <!-- <q-space/> -->
        <!-- </q-toolbar> -->
      </q-footer>
    </q-layout>
  </div>
</template>

<script>
import LeftDrawer from '../components/drawers/LeftDrawer'
import RightDrawer from '../components/drawers/RightDrawer'
import whatsapp from '../components/whatsapp/Dynamicwhatsapp'
// import FadeTransition from './FadeTransition.vue'

export default {
  components: {
    LeftDrawer,
    RightDrawer,
    whatsapp
    // FadeTransition
  },
  data () {
    return {
      headerTransitionVal: false,
      headerTransitionVal2: false,
      tabVal: false,
      // headerTransition: false,
      left: false,
      right: false,
      showWallE: true,
      // darkThemeBGColor: '#000',
      // darkThemeColor: '#f6f6f6',
      // lightThemeBGColor: '#f6f6f6',
      // lightThemeColor: '#000000',
      palette: ['#FFFFFFFF', '#F2C037FF', '#21BA45FF', '#26A69AFF', '#31CCECFF', '#1976D2FF', '#e600e2ff', '#512fa9ff', '#aa0000ff', '#242424ff']
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  // watch: {
  //   headerTransition () {
  //     this.headerTrans = true
  //     // setTimeout(() => this.headerTransition = true, 500)
  //     setTimeout(function () {
  //       this.headerTrans = false
  //     }, 1000)
  //     // this.headerTransition()
  //     // this.headerTransition = this.headerTransition
  //     // setTimeout(() => this.headerTransition = true, 500)
  //     // setTimeout(function () {
  //     //   this.headerTransition()
  //     // }, 1000)
  //     // this.fullName = val + ' ' + this.lastName
  //   }
  //   // lastName: function (val) {
  //   //   this.fullName = this.firstName + ' ' + val
  //   // }
  // },
  methods: {
    headerTab () {
      this.tabVal = true
      // setTimeout(this.tabVal = false, 3000)
      // setTimeout(function () {
      //   this.tabVal = false
      // }, 1000)
      // setTimeout(function () { this.tabVal = false }, 2000)
    },
    headerTransitionFunc (val) {
      this.headerTransitionVal2 = val
    //   // this.headerTransition = true
    //   // // setTimeout(() => this.headerTransition = true, 500)
    //   // setTimeout(function () {
    //   //   this.headerTransition = false
    //   // }, 1000)
    },
    handleScroll (event) {
      if (window.scrollY > 25) {
        this.headerTransition = true
      } else if (window.scrollY < 25 && this.tabVal === false) {
        this.headerTransition = false
      }
    },
    dynamicRoute (val) {
      const about = 'about'
      const services = 'services'
      const doubts = 'doubts'
      if (this.$route.fullPath.search(/\babout\b/) >= 0) {
        this.$router.push(val + '/' + about)
      } else if (this.$route.fullPath.search(/\bservices\b/) >= 0) {
        this.$router.push(val + '/' + services)
      } else if (this.$route.fullPath.search(/\bdoubts\b/) >= 0) {
        this.$router.push(val + '/' + doubts)
      } else {
        this.$router.push(val)
      }
    }
  },
  computed: {
    // headerTab: {
    //   get () {
    //     return this.tabVal
    //   },
    //   set () {
    //     this.tabVal = true
    //     setTimeout(function () { this.tabVal = false }, 2000)
    //   }
    // },
    headerTransition: {
      get () {
        return this.headerTransitionVal
      },
      set (val) {
        this.headerTransitionVal = val
        // this.headerTransitionVal2 = val
        setTimeout(this.headerTransitionFunc(val), 20000)
        // setTimeout(function () { this.headerTransitionVal2 = val }, 1000)
        // setTimeout(function () {
        //   // this.headerTransitionVal2 = !val
        // }, 1000)
      }
    },
    returnStyle: {
      get () {
        if (this.setStyle === false) {
          return { height: '96vh' }
        } else {
          return { height: '96vh' }
        }
      }
    }
  }
}
</script>

<style>
</style>
