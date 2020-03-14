<template>
  <div ref="wrap">
      <div class='guarantee' v-bind:style="{'height': $isIPad ? '142wx': '284px'}" @click='openArtificial'>
        <bui-image src="/image/guarantee.png" width="750px" :height="height" @click='openArtificial'></bui-image>
      </div>
  </div>
</template>

<script>
  const linkapi = require("linkapi");
  const dom = weex.requireModule("dom");
  export default {
    data() {
      return {
        height: '212px',
        channel: new BroadcastChannel("WidgetsMessage"),
      }
    },
    created() {
        this.height = this.$isIPad ? '106wx' : '212px'
    },
    mounted() {
        this.broadcastWidgetHeight()
    },
    methods: {
        openArtificial(){
            linkapi.openOnlineServicer()
        },
        getComponentRect(_params) {
            var that = this
            dom.getComponentRect(this.$refs.wrap, (ret) => {
                this.channel.postMessage({
                    widgetHeight: ret.size.height,
                    id: _params.id
                });
            });
        },
        broadcastWidgetHeight() {
            let _params = this.$getPageParams();
            // 防止高度通知失败
            setTimeout(() => {
                this.getComponentRect(_params)
            }, 200)
            setTimeout(() => {
                this.getComponentRect(_params)
            }, 1200)
        }
    }
  }
</script>

<style lang="css" src="../css/common.css"></style>
<style>
.guarantee {
    background: #fff;
}
</style>