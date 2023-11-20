<template>
  <div class="container">
    <div class="article-container">
      <h1 class="article-title">{{ article.title }}</h1>

      <div class="article-content">
        <div class="article-image">
          <NuxtImg
            v-show="isLoaded"
            @load="handleImageLoaded"
            class="article-image-item"
            :src="article.image"
            alt="image article"
          />

          <NuxtImg
            v-if="!isLoaded"
            src="https://loremflickr.com/cache/resized/65535_52961568320_cc849e66ed_z_640_480_nofilter.jpg"
            class="default-image"
          />
        </div>

        <div class="article-description">
          <div class="article-description__about">About</div>
          <p class="article-description__text">{{ article.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="js">
const { id } = useRoute().params;

const url = "https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/" + id;

const { data: article } = await useFetch(url);

const isLoaded = ref(false);

function handleImageLoaded() {
  return (isLoaded.value = true);
}
</script>

<style scoped lang="scss">
.article-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 70px;
  margin-bottom: 80px;
}
.article {
  margin-bottom: 20px;

  &-title {
    font-size: 84px;
    font-weight: 400;
    line-height: 84px;
    margin-bottom: 33px;
    text-align: center;

    @media screen and (max-width: 1024px) {
      font-size: 60px;
    }

    @media screen and (max-width: 520px) {
      font-size: 30px;
    }
  }

  &-content {
    margin-top: 40px;
  }

  &-description {
    width: 60%;

    &__about {
      font-size: 16px;
      margin-bottom: 32px;
    }
    &__text {
      font-size: 36px;
    }
  }
}

.article-image {
  display: flex;
  justify-content: center;
  margin-bottom: 80px;
}
.article-image-item {
  width: 100%;
}

.message-error {
  display: block;
  color: red;
  font-size: 12px;
  margin-bottom: 25px;
}

.default-image {
  width: 100%;
}
</style>
