<template>
  <div class="articles" @click="closeDropdown">
    <h1 class="articles__title">Articles</h1>

    <div class="articles-list">
      <div
        class="article"
        v-for="article in paginatedArticles"
        :key="article.id"
      >
        <ArticlesArticleItem :article="article" />
      </div>
    </div>

    <ArticlesArticlePagination
      @click.stop
      :currentPage="currentPage"
      :setCurrentPage="setCurrentPage"
      :totalPages="totalPages"
    />

    <div class="articles__not-found" v-if="!articles?.length">
      Ничего не найдено
    </div>
  </div>
</template>

<script setup lang="ts">
interface Article {
  id: number;
  title: string;
  image: string;
}

const { data: articles } = await useAsyncData<Article[]>("articles", () =>
  $fetch("https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/")
);

const articlesPerPage = ref(8);
const currentPage = ref(1);
const totalPages = computed(() =>
  Math.ceil((articles.value?.length ?? 0) / articlesPerPage.value)
);

const dropdownOpen = ref(false);

const paginatedArticles = computed(() => {
  const startIndex = (currentPage.value - 1) * articlesPerPage.value;
  const endIndex = startIndex + articlesPerPage.value;
  return articles.value?.slice(startIndex, endIndex) ?? [];
});

function setCurrentPage(page: number) {
  currentPage.value = page;
}

function closeDropdown() {
  dropdownOpen.value = false;
}
</script>

<style scoped lang="scss">
.articles {
  padding-bottom: 140px;
  &__title {
    margin-bottom: 59px;
    font-size: 84px;
    font-weight: 400;
  }

  &-list {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 2.3%;

    .article {
      width: 23%;
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;
      cursor: pointer;
      margin-bottom: 50px;
      position: relative;

      @media screen and (max-width: 1024px) {
        width: 30%;
        margin-bottom: 35px;
      }

      @media screen and (max-width: 768px) {
        width: 45%;
        margin-bottom: 25px;
      }

      @media screen and (max-width: 520px) {
        width: 70%;
        margin-bottom: 0px;
      }
    }
  }

  &__not-found {
    width: 100%;
    font-size: calc(24px + 11 * (100vw / 1280));
    text-align: center;
    color: red;
  }
}
</style>
