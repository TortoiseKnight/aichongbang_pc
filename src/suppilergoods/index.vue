<template>
  <div>
    <SupGoodsAdd></SupGoodsAdd>
    <SupGoodsList></SupGoodsList>
    <SupGoodsUpdate></SupGoodsUpdate>
  </div>
</template>
<script>
import axios from "axios";
import SupGoodsAdd from "./supGoodsAdd";
import SupGoodsList from "./supGoodsList";
import SupGoodsUpdate from "./supUpdate";

import { createNamespacedHelpers } from "vuex";
const { mapActions, mapMutations } = createNamespacedHelpers("supgoodsModule");
export default {
  data() {
    return {
      supgoods: []
      // supId: ""
    };
  },
  created: function() {
    this.getSession();
  },
  methods: {
    ...mapMutations(["setId"]),
    ...mapActions(["setSupGoods", "setID"]),
    getSession() {
      axios({
        method: "get",
        url: "/getSession"
      }).then(({ data }) => {
        let supId = data.user._id;
        console.log(data.user);
        axios({
          method: "get",
          url: "/suppiler"
        }).then(({ data }) => {
          for (let i = 0; i < data.length; i++) {
            if (supId == data[i].supp_number) {
              // let ids = this.setId();
              this.setID(data[i]._id);
              this.setSupGoods();
            }
          }
        });
      });
    }
  },
  components: {
    SupGoodsAdd,
    SupGoodsList
  }
};
</script>
<style>
</style>
