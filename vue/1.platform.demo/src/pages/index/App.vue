<template>
  <div id="app">
    <div class="header">
      <div class="logo">{{ logo }}</div>
      <ul class="menu">
        <li>
          <a href="http://localhost:8989">{{$t('L.APP_INDEX')}}</a>
        </li>
        <li>
          <a href="http://localhost:8989/page1.html#/">使用说明</a>
        </li>
        <li>
          <a href="https://cn.vuejs.org/" target="_blank">Vue社区</a>
        </li>
        <li>
          <a class="icon-github" style="font-size: 20px;"
             href="https://github.com/JHerculesqz/demo-js-vue" target="_blank"></a>
        </li>
        <li>
          <a class="icon-twitter" style="font-size: 20px;"
             href="https://github.com/JHerculesqz/demo-js-vue" target="_blank"></a>
        </li>
        <li>
          <a class="icon-droplet" style="font-size: 20px;" v-on:click="onThemeChange"></a>
        </li>
        <li>
          <a class="icon-marvelIcon-69" style="font-size: 20px;"
             @click="onLangChange"></a>
        </li>
      </ul>
    </div>
    <div class="content">
      <transition name="slide-fade">
        <router-view></router-view>
      </transition>
    </div>
    <div class="footer">
      footer
    </div>
  </div>
</template>

<script>
  import SkinUtilsEx from "~~/component/skin";
  import I18nUtilsEx from "~~/component/i18n";

  export default {
    name: 'app',
    data: function () {
      return {
        //#region logo
        logo: "Fuck UI 3.0",
        //#endregion
      }
    },
    mounted: function () {
      //#region custom

      //#endregion
    },
    methods: {
      //#region inner

      //#endregion

      //#region theme

      onThemeChange: function () {
        var bIsDark = SkinUtilsEx.getCurrentTheme() == "dark";
        if (bIsDark) {
          SkinUtilsEx.themeChange("");
        } else {
          SkinUtilsEx.themeChange("dark");
        }
      },

      //#endregion

      //#region language

      onLangChange: function () {
        var bIsZh = I18nUtilsEx.getCurrentLocal(this.$i18n) == "zh";
        if (bIsZh) {
          I18nUtilsEx.localeChange(this.$i18n, "en");
        } else {
          I18nUtilsEx.localeChange(this.$i18n, "zh");
        }
      }

      //#endregion
    }
  }
</script>

<style>
  html, body {
    width: 100%;
    height: 100%;
    overflow: hidden;
  }

  body {
    position: fixed;
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    font-family: Tahoma, Arial, Roboto, ”Droid Sans”, ”Helvetica Neue”, ”Droid Sans Fallback”, ”Heiti SC”, sans-self;
  }

  ol, ul {
    list-style: none;
  }

  #app {
    height: 100%;
  }

  .header {
    width: 100%;
    height: 50px;
    position: absolute;
    top: 0;
    left: 0;
    background-color: #3b2e49;
    z-index: 999;
  }

  .header .logo {
    width: 240px;
    height: 100%;
    float: left;
    /*color: #007df9;*/
    color: #ffaa00;
    font-size: 26px;
    font-weight: bold;
    line-height: 50px;
    text-align: center;
  }

  .header ul {
    margin: 0;
    padding: 0;
    float: right;
    margin-right: 40px;
  }

  .header ul li {
    float: left;
    margin-right: 10px;
    margin-top: 0;
    list-style-type: none
  }

  .header ul li a {
    line-height: 50px;
    /*color: #666;*/
    color: #ffffff;
    font-size: 14px;
    padding: 0 10px;
    text-decoration: none;
  }

  .header ul li .active {
    color: #ffaa00;
  }

  .content {
    height: 100%;
    position: relative;
  }

  .footer {
    height: 0px;
    background-color: #e8e8e8
  }

  .slide-fade-enter-active {
    transition: all .3s ease;
  }

  .slide-fade-leave-active {
    transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }

  .slide-fade-enter, .slide-fade-leave-active {
    transform: translateX(-430px);
    opacity: 0;
  }
</style>
