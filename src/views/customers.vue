<template>
    <div class="customers">
        <h1>customers</h1>
 <b-table striped hover :items="products" :fields="fields" :per-page="pagesize" :current-page="pageindex"></b-table>
  <b-pagination size="lg" :total-rows="products.length" v-model="pageindex" :per-page="pagesize">  </b-pagination>
    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "customers",
  components: {},
  data() {
    return {
      message: "customers",
      products: [],
      pagesize:5,
      pageindex:1,
      fields: [
        { key: "customers_id", sortable: true },
        { key: "company_name", sortable: true },
        { key: "contact_name", sortable: true },
        { key: "contact_title", sortable: true },
        { key: "address", sortable: true },
        { key: "city", sortable: true },
        { key: "pegion", sortable: true },
        { key: "postal_code", sortable: true },
        { key: "country", sortable: true },
        { key: "phone", sortable: true },
        { key: "fax", sortable: true, variant: "danger" }
      ]
    };
  },
  mounted() {
    var instace = this;
    axios
      .get("https://tranquil-brook-45115.herokuapp.com/api/Customers/")
      .then(function(response) {
        console.log(response.data);
        instace.products = response.data.data;
      });
  }
};
</script>