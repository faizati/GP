<template>
  <div id="siteFooter">
    <div class="container">
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-bottom">
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="nav navbar-nav" style="margin:auto;">
            <!-- <li v-for="item in items" class="nav-item">  <a class="nav-link pr-5 pl-5"> <router-link :to="item.url" tag="li" active-class="active" exact>{{ item.title }}</router-link> </a> </li> -->
            <router-link
              :to="item.url"
              tag="li"
              active-class="active"
              exact
              v-for="(item, index) in items"
              :key="index"
            >
              <a class="nav-link pl-5 pr-5 ml-3 mr-3">{{ item.title }}</a>
            </router-link>
          </ul>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
const menus = [
  { title: "Home", url: "/" },
  { title: "Project", url: "/project" },
  { title: "invoice", url: "/invoice" },
  { title: "Supplier", url: "/supplier" },
  { title: "Customer", url: "/customer" },
  { title: "Login", url: "/login" }
];
export default {
  name: "siteFooter",
  data: function() {
    return {
      items: [...menus],
      selectedLink: "Home"
    };
  },
  computed: {
    ...mapGetters(["user"])
  },
  watch: {
    user(val) {
      const test = this.items.filter(menu => menu.title !== "Login");
      if (val !== null)
        this.items = this.items.filter(menu => menu.title !== "Login");
      else this.items = menus;
    }
  }
};
</script>

<style scoped>
a {
  color: white;
  text-transform: uppercase;
  text-align: center;
}
a:hover {
  background: #565c61;
  border-radius: 5px;
  text-decoration: none;
}
.active {
  background: #565c61;
  border-radius: 5px;
}
</style>