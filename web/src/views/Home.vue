<template>
  <div class="container">
    <!-- content row-->
    <!-- left column-->
    <div class="col-sm-2">
      <h2>Cat</h2>
      <div id="categoryList" class="list-group">
        <a class="list-group-item list-group-item-action">Items</a>
      </div>
    </div>
    <!-- end left col-->
    <!-- Right column -->
    <div class="col-sm-10">
      <table
        id="MyTable"
        class="table table-striped table-bordered table-hover"
      >
        <tbody>
          <tr>
            <td>Text</td>
            <td>Type</td>
            <td>Upvotes</td>
          </tr>
          <tr v-for="f in tenFacts" v-bind:key="f._id">
            <td>
              <router-link
                :to="{ name: 'Categories', params: { id: f._id, fact: f } }"
                >{{ f.text }}</router-link
              >
            </td>
            <td>{{ f.type }}</td>
            <td>{{ f.upvotes }}</td>
          </tr>
        </tbody>
      </table>
      <button @click="sortLowest">Lowest</button>
      <button @click="sortHighest">Highest</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      facts: null,
      fact: null,
      users: null,
      User: null
    };
  },
  computed: {
    tenFacts() {
      return this.facts ? this.facts.slice(0, 10) : [];
    }
  },
  methods: {
    loadData() {
      axios.get("https://cat-fact.herokuapp.com/facts").then(response => {
        this.facts = response.data.all;
        axios.get("https://cat-fact.herokuapp.com/users/me").then(response => {
          this.users = response.data.all;
        });
      });
    },
    setSelected(newVal) {
      this.fact = newVal;
    },
    sortLowest() {
      this.facts.sort((a, b) => (a.facts > b.facts ? 1 : -1));
    },
    sortHighest() {
      this.facts.sort((a, b) => (a.facts > b.facts ? 1 : -1));
    }
  },
  mounted() {
    this.loadData();
  }
};
</script>
<style scoped>
.container {
  display: flex;
}
</style>
