<template>
  <div class="widgetShowSession">
    <!--1级 start-->
    <div class="title level1">MarvelLoadingMini</div>
    <div class="describe">

    </div>
    <!--1级 end-->
    <!--region widget show area-->
    <!--2级 start-->

    <div class="showArea">
      <marvel-tab :tabItems="tabItems1">
        <marvel-tab-item :isActive="tabItems1[0].isActive">
          <div class="showAreaInner">
            <!--2级DemoView start-->
            <button v-on:click="showEx">show</button>
            <button v-on:click="setProgress">setProgress</button>
            <button v-on:click="hideEx">hide</button>
            <marvel-loading-mini ref="ref0" v-on:onCancel="loadingOnCancel"></marvel-loading-mini>
            <!--2级DemoView end-->
          </div>
        </marvel-tab-item>
        <marvel-tab-item :isActive="tabItems1[1].isActive">
          <div class="codeArea">
            <marvel-ace-editor ref="aceEditor" theme="dracula" :fontSize="15" :readOnly="true" lan="html" codeIn='
            <button v-on:click="showEx">show</button>
            <button v-on:click="setProgress">setProgress</button>
            <button v-on:click="hideEx">hide</button>
            <marvel-loading-mini ref="ref0" v-on:onCancel="loadingOnCancel"></marvel-loading-mini>
            '></marvel-ace-editor>
          </div>
        </marvel-tab-item>
      </marvel-tab>
    </div>
    <!--2级 end-->
    <!--endregion-->
    <!--region doc area-->
    <div class="docArea">
      <marvel-i-frame ref="page4MarvelLoadingMiniIFrame" id="page4MarvelLoadingMiniIFrame" src="static/jsdoc/module-MarvelLoadingMini.html"></marvel-i-frame>
    </div>
    <!--endregion-->
  </div>
</template>

<script>
  import MarvelTab from "~~/widget/tab/MarvelTab";
  import MarvelTabItem from "~~/widget/tab/MarvelTabItem";
  import MarvelAceEditor from "~~/widget/aceEditor/MarvelAceEditor";
  import MarvelLoadingMini from "^/widget/loading/MarvelLoadingMini";
  import MarvelIFrame from "../../../../../components/MarvelIFrame";

  export default {
    name: 'page4MarvelLoadingMini',
    components: {
      MarvelLoadingMini,
      MarvelIFrame,
      MarvelAceEditor,
      MarvelTab,
      MarvelTabItem,
    },
    data: function () {
      return {
        //#region document data
        tabItems1: [{
          label: "Demo View",
          isActive: true
        }, {
          label: "Code View",
          isActive: false
        }],
        //#endregion
        //#region custom data

        //#endregion
      }
    },
    mounted: function () {
      //#region init

      this._initEx();

      //#endregion
    },
    methods: {
      //#region inner

      //#region lifeCycle

      _initEx: function () {
        this.$refs.page4MarvelLoadingMiniIFrame.setIframe4DemoPage();
      },

      //#endregion

      showEx: function(){
        this.$refs.ref0.showEx("取消");
      },
      setProgress: function(){
        var self = this;
        self.$refs.ref0.setProgress(10, "step1...");
        setTimeout(function(){
          self.$refs.ref0.setProgress(30, "step2...");
          setTimeout(function(){
            self.$refs.ref0.setProgress(60, "step3...");
            setTimeout(function(){
              self.$refs.ref0.setProgress(100, "step4...");
            },1000);
          },1000);
        },1000);
      },
      hideEx: function(){
        this.$refs.ref0.hideEx();
      },
      //#endregion
      //#region callback
      loadingOnCancel:function(){
        console.log("loadingCancel");
      }

      //#endregion
      //#region callback
      //#endregion
      //#region 3rd
      //#endregion
    }
  }
</script>

<style scoped>
  /*document fix style start*/
  .widgetShowSession {
    padding: 20px 100px;
    width: 100%;
    box-sizing: border-box;
  }

  .title {
    color: #4d4d4d;
  }

  .level1 {
    font-size: 32px;
    line-height: 54px;
  }

  .describe {
    font-size: 14px;
    color: #666;
    line-height: 36px;
  }

  .codeArea {
    width: 100%;
    height: 100%;
    background-color: #f0f0f0;
    overflow: auto;
  }

  .showAreaInner {
    box-sizing: border-box;
  }

  .docArea{
    width: 100%;
  }

  .docArea iframe{
    width: 100%;
    height: 100%;
    border: none;
  }

  /*document fix  style end*/
  /*document custom style start*/
  .showArea {
    height: 400px;
  }

  /*document custom style end*/
  /*custom style start*/

  /*custom style end*/

  /*region dark theme*/

  .dark .title {
    color: #ffffff;
  }

  .dark .describe {
    color: #8b90b3;
  }

  /*endregion*/
</style>
