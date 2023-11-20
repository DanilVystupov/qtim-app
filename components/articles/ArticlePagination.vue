<template>
  <div class="pagination">
    <button
      class="pagination__item"
      v-for="page in visiblePages"
      :key="page"
      @click="setCurrentPage(page)"
      :class="{ isActive: currentPage === page }"
    >
      {{ page }}
    </button>

    <div class="dropdownPages" v-show="dropdownOpen" @click.stop>
      <button
        v-for="page in dropdownPages"
        :key="page"
        @click="setCurrentPage(page)"
        class="pagination__item"
        :class="{ isActive: currentPage === page }"
      >
        {{ page }}
      </button>
    </div>

    <button
      :class="[
        dropdownOpen ? 'pagination__showMore rotate' : 'pagination__showMore',
      ]"
      @click.stop="toggleDropdown"
    >
      <NuxtImg
        src="images/arrow-right.png"
        alt="arrow-right"
        width="24"
        height="24"
      />
    </button>
  </div>
</template>

<script setup lang="ts">
interface Props {
  currentPage: number;
  totalPages: number;
  setCurrentPage: (page: number) => void;
}

const { currentPage, totalPages, setCurrentPage } = defineProps<Props>();

const dropdownOpen = ref(false);

const dropdownPages = computed(() => {
  const totalPagesValue = totalPages;
  const pages = Array.from(
    { length: totalPagesValue },
    (_, index) => index + 1
  );
  if (totalPagesValue <= 5) {
    return [];
  } else {
    return pages.slice(5, totalPagesValue);
  }
});

const visiblePages = computed(() => {
  const totalPagesValue = totalPages;
  if (totalPagesValue <= 5) {
    return Array.from({ length: totalPagesValue }, (_, index) => index + 1);
  } else {
    return [1, 2, 3, 4, 5];
  }
});

function toggleDropdown() {
  dropdownOpen.value = !dropdownOpen.value;
}
</script>

<style scoped lang="scss">
.pagination {
  display: flex;
  align-items: center;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 140px;
  &__item {
    width: 44px;
    height: 44px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
    border-radius: 12px;
    color: rgba(16, 16, 16, 1);
    cursor: pointer;
  }

  &__showMore {
    width: 44px;
    height: 44px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
    border: 1px solid rgba(232, 232, 232, 1);
    border-radius: 12px;
    color: rgba(16, 16, 16, 1);
    cursor: pointer;

    &:hover {
      background-color: rgba(232, 232, 232, 1);
    }
  }

  .rotate {
    transform: rotateY(180deg);
  }

  .isActive {
    background-color: rgba(16, 16, 16, 1);
    color: rgba(255, 255, 255, 1);
  }
}

.dropdownPages {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  flex-wrap: wrap;
}
</style>
