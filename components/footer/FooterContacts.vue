<template>
  <div class="footer-links">
    <nav class="footer-links-nav">
      <ul class="footer-links-nav__list">
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Facebook</li>
        </NuxtLink>
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Instagram</li>
        </NuxtLink>
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Telegram</li>
        </NuxtLink>
      </ul>
    </nav>

    <div class="footer-links__going">Go</div>

    <nav class="footer-links-nav">
      <ul class="footer-links-nav__list">
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Behance</li>
        </NuxtLink>
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Linkedn</li>
        </NuxtLink>
        <NuxtLink to="/">
          <li class="footer-links-nav__list-item">Privacy Policy</li>
        </NuxtLink>
      </ul>
    </nav>
  </div>
</template>

<style scoped lang="scss">
.footer-links {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 30px;
  position: relative;

  @media screen and (max-width: 1024px) {
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 25px;
  }

  &-nav {
    &__list {
      display: flex;
      width: 100%;
      gap: 32px;

      &-item {
        text-decoration: underline;
        text-decoration-thickness: 1px;
        text-underline-offset: 11px;
        cursor: pointer;
        transition: color 0.4s;

        &:hover {
          color: white;
        }
      }
    }
  }
  &__going {
    font-size: 32px;
    font-weight: 400;
    color: white;
    z-index: 1;

    @media screen and (max-width: 1024px) {
      display: none;
    }

    &::before {
      content: "";
      position: absolute;
      bottom: -179px;
      left: 50%;
      transform: translateX(-50%);
      width: 358px;
      height: 358px;
      background-color: rgba(16, 16, 16, 1);
      border-radius: 50% 50% 0 0;
      text-align: center;
      line-height: 358px;
      font-weight: bold;
      color: #ffffff;
      font-size: 32px;
      z-index: -1;
    }
  }
}
</style>
