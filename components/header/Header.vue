<template>
  <!-- Header Section Begin -->
  <header class="header">
    <div class="container">
      <div class="row">
        <div class="col-lg-6">
          <div class="header__logo">
            <nuxt-link tag="h1" to="/">movieReview</nuxt-link>
          </div>
        </div>
        <div class="col-lg-6">
          <nav class="header__menu">
            <ul>
              <li>
                <nuxt-link tag="a" to="/add-movie">Add New Movie</nuxt-link>
              </li>
              <li>
                <nuxt-link
                  tag="a"
                  to="/user/login"
                  class="header-nav__link"
                  v-if="!$store.getters.isAuthenticated"
                >
                  Login
                </nuxt-link>
              </li>
              <li>
                <a
                  class="header-nav__link"
                  v-if="$store.getters.isAuthenticated"
                  @click="logout"
                >
                  Logout
                </a>
              </li>
              <li>
                <a
                  class="header-nav__link"
                  v-if="$store.getters.isAuthenticated"
                >
                  {{ $store.state.userData.username }}
                </a>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </header>
  <!-- Header Section End -->
</template>
<script>
export default {
  methods: {
    logout() {
      this.$store.commit("setToken", null);
      this.$router.push("/");
    },
  },
};
</script>
<style>
.header__logo {
  padding: 15px 0;
}

.header__logo img {
  width: 200px;
  padding-top: 10px;
}

.header__logo a {
  display: inline-block;
}

.header__menu {
  padding: 24px 0;
}

.header__menu ul li {
  list-style: none;
  margin-right: 50px;
  position: relative;
  text-align: right;
}

.header__menu ul li:hover > a {
  color: #7fad39;
}

.header__menu ul li:last-child {
  margin-right: 0;
}

.header__menu ul li a {
  font-size: 14px;
  color: #252525;
  text-transform: uppercase;
  font-weight: 700;
  letter-spacing: 2px;
  transition: all, 0.3s;
  padding: 5px 0;
  display: block;
}
</style>
