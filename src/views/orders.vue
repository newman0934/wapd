<template>
  <div class="container mt-4">
    <div v-if="isLoading">
      <spinner />
    </div>
    <div v-else>
      <div v-if="filterOrders.length == 0">
        <h3 class="mt-4">您目前無訂購紀錄喔，快去商場看看吧！</h3>
      </div>
      <div v-else>
        <table class="table table-striped">
          <thead>
            <tr>
              <th scope="col">訂單編號</th>
              <th scope="col">總計</th>
              <th scope="col">付款狀態</th>
              <th scope="col">運送狀態</th>
              <th scope="col">備註</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="order in filterOrders" :key="order.id">
              <th scope="row" class="align-middle">
                <router-link :to="{name:'order', params:{ order_id:order.id }}">#{{order.sn}}</router-link>
                <p>@{{order.createdAt | timeFormate}}</p>
              </th>
              <td class="align-middle">
                NTD {{order.total_price}}
                <!-- <p>商品總數量：{{order.OrderItems.length}}</p> -->
              </td>
              <td class="align-middle">{{order.payment_status==1 ? "已付款" : "未付款"}}</td>
              <td class="align-middle">{{order.shipping_status==0? "尚未出貨": "其他"}}</td>
              <td class="align-middle">
                <p v-if="!order.total_price">
                  尚未收到您的訂單，您可
                  <br />
                  <button
                    class="btn btn-sm btn-outline-dark"
                    @click="continuousOrder(order.id)"
                  >繼續下單</button>
                </p>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
import usersAPI from "./../apis/users";
import spinner from "./../components/spinner";
import { mapState } from "vuex";
import { timeFilter } from "./../utils/mixins";
import { Toast } from "./../utils/helpers";
export default {
  mixins: [timeFilter],
  components: {
    spinner
  },
  data() {
    return {
      orders: []
    };
  },
  computed: {
    ...mapState(["currentUser", "isLoading"]),
    filterOrders() {
      return this.orders
        .filter(order => order.payment_status !== "99")
        .sort((a, b) => b.id - a.id);
    }
  },
  created() {
    this.fetchUserOrders();
  },
  methods: {
    async fetchUserOrders() {
      try {
        this.$store.dispatch("updateLoading", true);
        const { data, statusText } = await usersAPI.getUserOrders();
        if (statusText !== "OK") {
          throw new Error(statusText);
        }
        this.orders = data.orders;
        this.$store.dispatch("updateLoading", false);
      } catch (error) {
        this.$store.dispatch("updateLoading", false);
        Toast.fire({
          icon: "error",
          title: "無法取得訂單資料，請稍後再試"
        });
      }
    },
    continuousOrder(id) {
      this.$router.push({ name: "checkout", params: { id } });
    }
  }
};
</script>