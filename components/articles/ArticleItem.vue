<template>
  <div class="article-wrap">
    <NuxtLink v-if="props.article" :to="`articles/${props.article.id}`">
      <div>
        <NuxtImg
          v-show="isLoaded"
          @load="handleImageLoaded"
          class="article-wrap__image"
          :src="props.article.image"
          alt="image"
        />
      </div>

      <div>
        <NuxtImg
          v-if="!isLoaded"
          src="https://loremflickr.com/cache/resized/65535_52961568320_cc849e66ed_z_640_480_nofilter.jpg"
          title="Не удалось загрузить изображение"
          class="article-wrap__image"
        />
      </div>

      <div class="article-wrap__text" v-if="props.article.title">
        {{ props.article.title.slice(0, 94) }}...
      </div>

      <div class="article-wrap__button">
        <button class="article-wrap__button-item">Read more</button>
      </div>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
interface ArticleItem {
  id: number;
  title: string;
  image: string;
}

const props = defineProps({
  article: Object as () => ArticleItem,
});

const isLoaded = ref(false);

function handleImageLoaded() {
  return (isLoaded.value = true);
}
</script>

<style scoped lang="scss">
.article-wrap {
  display: flex;
  flex-direction: column;
  height: 250px;

  &:hover {
    .article-wrap__button {
      display: block;

      @media screen and (max-width: 768px) {
        display: none;
      }
    }

    margin-bottom: 50px;

    @media screen and (max-width: 1024px) {
      margin-bottom: 30px;
    }

    @media screen and (max-width: 768px) {
      margin-bottom: 0;
    }
  }
  &__image {
    width: 100%;
    height: auto;
  }

  &__text {
    font-size: 20px;
    margin-top: 24px;
    margin-bottom: 12px;
  }

  &__button {
    display: none;
    animation: opacity 0.7s forwards;

    @keyframes opacity {
      0% {
        opacity: 0;
      }
      100% {
        opacity: 1;
      }
    }

    &-item {
      border: none;
      background: none;
      font-weight: 400;
      font-size: 20px;
      color: rgba(226, 190, 255, 1);
      cursor: pointer;
    }
  }
}

.message-error {
  display: block;
  color: red;
  font-size: 12px;
  margin-bottom: 25px;
}
</style>
