<template>
  <div class="header-right">
    <button class="header-right__item">
      <NuxtImg src="images/UK.png" alt="UK" width="24" height="24" />
    </button>
    <button class="header-right__item">Let’s work</button>
  </div>
</template>

<style scoped lang="scss">
.header-right {
  width: 45%;
  display: flex;
  justify-content: end;
  align-items: center;
  gap: 16px;

  @media screen and (max-width: 768px) {
    width: 100%;
  }

  &__item:nth-child(1) {
    width: 52px;
    height: 52px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
    border-radius: 999px;
    border: 2px solid rgba(0, 0, 0, 0.1);
    cursor: pointer;

    @media screen and (max-width: 768px) {
      width: 45px;
      height: 45px;
    }
  }

  &__item:nth-child(2) {
    padding: 16px 32px;
    background-color: rgba(16, 16, 16, 1);
    color: white;
    border: transparent;
    border-radius: 999px;
    cursor: pointer;
    transition: background-color 0.5s;

    &:hover {
      background-color: rgba(226, 190, 255, 1);
      color: black;
    }

    @media screen and (max-width: 768px) {
      display: none;
    }
  }
}
</style>
