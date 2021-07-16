<template>
  <header class="navbar">
    <a
      href="/"
      class="logo"
    >Rick and Morty Characters</a>

    <!-- <nav>
      <ul>
        <li>
          <router-link to="/">Home</router-link>
        </li>
        <li>
          <router-link to="/about">About</router-link>
        </li>
      </ul>
    </nav> -->

  </header>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style lang="scss" scoped>
// Imports
@import "../styles/variables";

header {
  width: 100%;
  height: 100px;
  padding: 0 $px;
  margin-bottom: 30px;
  background-color: $color-primary;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0px 2px 8px rgba(#000, 0.3);

  .logo {
    width: 200px;
    color: $color-light;
    font-size: 22px;
  }

  nav ul {
    display: flex;
    justify-content: space-between;

    li:not(:last-child) {
      margin-right: 20px;
    }

    li a {
      color: $color-secondary;
      font-weight: bold;

      &.router-link-active {
        border-bottom: 2px solid $color-light;
      }
    }
  }
}

// Media Queries
@media (max-width: 768px) {
  header {
    padding: 0 $px-sm;

    .logo {
      font-size: 18px;
    }
  }
}
</style>