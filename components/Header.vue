<template>
  <div>
    <header class="header">
      <font-awesome-icon
        icon="fa-solid fa-bars"
        class="menu"
        @click="openNav"
      />

      <div class="logo">
        <h1>ShukrullojonDev</h1>
      </div>
    </header>

    <nav v-show="toggled" class="navigation">
      <div class="links">
        <NuxtLink class="link" to="/">Home</NuxtLink>
        <NuxtLink class="link" to="projects">Projects</NuxtLink>
        <NuxtLink class="link" to="contacts">Contacts</NuxtLink>
      </div>
      <font-awesome-icon
        icon="fa-solid fa-xmark"
        style="width: 20px; height: 20px"
        @click="closeNav"
      />
    </nav>
  </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data() {
    return {
      toggled: false,
    }
  },
  methods: {
    openNav() {
      this.toggled = true
    },
    closeNav() {
      this.toggled = false
    },
  },
}
</script>

<style scoped>
.header {
  padding-top: 20px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.menu {
  position: absolute;
  left: 0;
  width: 20px;
  height: 20px;
  padding-left: 10px;
}
.close {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
}
.navigation {
  position: absolute;
  top: 0;
  left: 0;
  background-color: grey;
  width: 280px;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  padding: 20px 20px 0 10px;
}
.links {
  display: flex;
  flex-direction: column;
}
.link {
  margin: 0 10px;
  text-decoration: none;
}
</style>
