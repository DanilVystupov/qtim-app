<template>
  <div class="footer">
    <div class="footer-left">
      <span class="footer-left__question">Is there a project?</span>
      <h2 class="footer-left__title">Let’s work together</h2>
    </div>

    <div class="footer-right">
      <div class="footer-right-info">
        <div class="footer-right-info__title">For all questions</div>
        <div class="footer-right-info__contacts">
          <div class="footer-right-info__contacts__item">
            +7 (920) 278—00—68
          </div>
          <div class="footer-right-info__contacts__item">qtim@agency.com</div>
        </div>
      </div>

      <div class="footer-right-info">
        <div class="footer-right-info__title">Office in Russia</div>
        <div class="footer-right-info__contacts">
          <div class="footer-right-info__contacts-item">
            139 Ruben Station Lake <br />
            Drew, NM 52678
          </div>
          <div class="footer-right-info__contacts-icon">
            <NuxtImg
              src="/images/Vector.svg"
              alt="telegram"
              width="12"
              height="12"
            />
          </div>
        </div>
      </div>

      <div class="footer-right-info">
        <div class="footer-right-info__title">Office in Dubai</div>
        <div class="footer-right-info__contacts">
          <div class="footer-right-info__contacts-item">
            139 Ruben Station Lake <br />
            Drew, NM 52678
          </div>
          <div class="footer-right-info__contacts-icon">
            <NuxtImg
              src="/images/Vector.svg"
              alt="telegram"
              width="12"
              height="12"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.footer {
  display: flex;
  justify-content: space-between;

  &-left {
    display: flex;
    flex-direction: column;
    gap: 56px;
    width: 60%;

    &__title {
      font-size: 112px;
      text-decoration: underline;
      text-decoration-thickness: 1px;
      text-underline-offset: 11px;

      @media screen and (max-width: 1024px) {
        font-size: 70px;
      }

      @media screen and (max-width: 768px) {
        font-size: 50px;
      }

      @media screen and (max-width: 520px) {
        font-size: 40px;
      }
    }
  }

  &-right {
    width: 35%;
    display: flex;
    flex-direction: column;

    &-info:not(:last-child) {
      margin-bottom: 36px;
    }

    &-info:last-child {
      margin-bottom: 273px;
    }

    &-info {
      &__title {
        margin-bottom: 12px;
      }

      &__contacts {
        &-item:first-child {
          margin-bottom: 4px;
        }

        &-icon {
          width: 32px;
          height: 32px;
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 999px;
          background-color: black;
          cursor: pointer;
        }
      }
    }
  }
}
</style>
