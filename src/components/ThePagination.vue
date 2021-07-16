<template>
  <div class="pagination">
    <div
      className="page-btns-container"
      v-if="pagination"
    >
      <button
        class="page-btn"
        v-if="pagination.prev"
        @click="$emit('get-page', pagination.prev)"
      >Previous</button>

      <!-- <span>
        1 / {{pagination.pages}}
      </span> -->

      <button
        class="page-btn"
        v-if="pagination.next"
        @click="$emit('get-page', pagination.next)"
      >Next</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pagination",
  props: {
    pagination: Object,
  },
};
</script>

<style lang="scss" scoped>
// Imports
@import "../styles/variables";

.pagination {
  width: 100%;
  margin-bottom: 30px;
  display: flex;
  justify-content: space-between;

  /*
  .clear-search-btn {
    height: 30px;
    padding: 0 20px;
    border-radius: 6px;
    border: none;
    background-color: #d66262;
    color: $color-secondary;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 14px;
    position: relative;
    cursor: pointer;
  }

  .clear-search-btn:hover {
    background-color: #a52f2f;
  }
  */

  .page-btns-container {
    width: 100%;
    display: flex;
    justify-content: flex-end;

    .page-btn {
      padding: 0 6px;
      height: 30px;
      border: none;
      border-radius: 6px;
      font-weight: bold;
      background-color: $color-primary;
      color: $color-light;
      cursor: pointer;

      &:last-child {
        margin-left: 8px;
      }
    }

    .page-btn:hover {
      background-color: $color-secondary;
    }

    span {
      height: 30px;
      margin: 0 8px;
      padding: 0 6px;
      border-radius: 6px;
      font-size: 14px;
      background-color: $color-light;
      color: darken($color-light, 40);
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}

// Media Queries
@media (max-width: 768px) {
  .pagination {
    padding: 0 $px-sm;
  }
}
</style>