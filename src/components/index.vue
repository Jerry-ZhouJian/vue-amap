<template>
  <div>
      <vue-amap :markers="markers"  style="width:1000px; height:800px"></vue-amap>
  </div>
</template>


<script>
import VueAmap from "@/components/VueAmap"
export default {
    data(){
        return {
            markers:[{
                position:[121.16487,31.02216],
                icon:"",
                title:"我是第一个点"
            },
            {
                position:[121.21433,30.96919],
                title:"我是第二个点"
            }
            ]
        }
    },
  components:{VueAmap}
}
</script>

<style>

</style>
