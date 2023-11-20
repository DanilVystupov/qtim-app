<template>
  <div class="header">
    <div class="header-left">
      <div class="header-left__logo">
        <NuxtLink to="/">
          <NuxtImg src="images/logo.svg" alt="Logo" width="84" height="25" />
        </NuxtLink>
      </div>

      <nav class="header-left-nav">
        <ul :class="[isOpenMenu ? 'nav-list active' : 'nav-list']">
          <NuxtLink to="/">
            <li class="nav-list__item">Works</li>
          </NuxtLink>
          <NuxtLink to="/">
            <li class="nav-list__item">About</li>
          </NuxtLink>
        </ul>
      </nav>
    </div>

    <HeaderButtons />

    <div class="burger-btn">
      <Icon
        v-if="isOpenMenu"
        @click="toggleMenu"
        icon="charm:cross"
        width="35"
        height="35"
      />
      <Icon
        v-else
        @click="toggleMenu"
        icon="iconamoon:menu-burger-horizontal"
        width="35"
        height="35"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { Icon } from "@iconify/vue";

const isOpenMenu = ref(false);
const toggleMenu = () => {
  isOpenMenu.value = !isOpenMenu.value;
};
</script>

<style scoped lang="scss">
.header {
  margin: 0 40px;
  padding: 50px 0;
  display: flex;
  justify-content: space-between;
}

.header-left {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;

  &__logo {
    cursor: pointer;
  }

  &-nav {
    .nav-list {
      display: flex;
      gap: 58px;

      @media screen and (max-width: 768px) {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 20px;
        position: fixed;
        left: -100%;
        right: 0;
        top: 0;
        bottom: 0;
        width: 100%;
        height: 100vh;
        background-color: rgb(85 85 110 / 90%);
        z-index: 10;
        transition: left 1s;
      }

      &__item {
        font-size: 20px;
        padding: 5px 5px;
        background-color: transparent;
        cursor: pointer;
        border-radius: 5px;
        transition: background-color 0.5s;

        &:hover {
          background-color: rgba(226, 190, 255, 1);
          border-radius: 5px;
        }
      }
    }
  }

  .active {
    left: 0;
  }
}

.burger-btn {
  display: none;

  @media screen and (max-width: 768px) {
    display: flex;
    align-items: center;
    margin-left: 3%;
    z-index: 10;
    cursor: pointer;
  }
}
</style>
