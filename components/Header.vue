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

    <nav class="navigation closeNavigation">
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
      const navigation = document.querySelector('.navigation')
      this.toggled = true
      navigation.classList.remove('closeNavigation')
      navigation.classList.add('openNavigation')
    },
    closeNav() {
      const navigation = document.querySelector('.navigation')
      this.toggled = false
      navigation.classList.remove('openNavigation')
      navigation.classList.add('closeNavigation')
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
.navigation {
  position: absolute;
  top: 0;
  left: 0;
  background-color: #393e46;
  width: 300px;
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
.closeNavigation {
  transform: translateX(-300px);
  animation-name: closed;
  animation-duration: 300ms;
}
.openNavigation {
  animation-name: opened;
  animation-duration: 300ms;
}

@keyframes opened {
  from {
    transform: translateX(-300px);
    visibility: visible;
  }
  99% {
    transform: translate(-1px);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes closed {
  from {
    transform: translateX(0);
  }
  99% {
    transform: translateX(-299px);
  }
  to {
    transform: translateX(-280px);
    visibility: hidden;
  }
}
</style>
