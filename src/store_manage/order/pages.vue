<template>
  <div class="num">
    <el-pagination background
      layout="prev, pager, next"
      :total="pagenation.total"
      class="yema"
      :page-size="pagenation.eachpage"
      @current-change="change"
    ></el-pagination>
  </div>
  
</template>

<script>
// import { mapState, mapMutations, mapActions } from "vuex";
export default {
  props:["pagenation","show"],
  methods:{
    change(value){
      console.log(value)
      this.show(value)
    }
  }

};
</script>

<style scoped>
.yema {
  float: left;
}
.num {
  margin-top: 20px;
}
</style>
