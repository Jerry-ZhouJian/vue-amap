<template>
  <div id="container"></div>
</template>

<script>
import AMap from "AMap";
export default {
  props:["markers"],
  data() {
    return {
      msg: "",
      // 地图实例
      VueAmap: {},
      // 窗体实例
      infoWindow:{}
    };
  },
  methods: {
    initMap() {
      this.VueAmap = new AMap.Map("container", {
        resizeEnable: true,
        zoom: 12,
        center: [121.606804,31.203125]
      });
      this.generateMarkers()
    },
    // 生成点
    generateMarkers() {
      for(var i=0;i<this.markers.length;i++){
       var marker = new AMap.Marker({
                position: this.markers[i].position,
                icon:this.markersIcon(this.markers[i].icon),
                title: this.markers[i].title,
                map: this.VueAmap
                });
      }
      this.VueAmap.setFitView();
    },
    // 点的icon属性
    markersIcon(src){
      var icon = ""
      if(src === undefined || src === ""){
        return icon
      }
      return icon = new AMap.Icon({
        image : src,//24px*24px
        //icon可缺省，缺省时为默认的蓝色水滴图标，
        size : new AMap.Size(24,24)
        });
    }
  },
  mounted() {
    this.initMap();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
