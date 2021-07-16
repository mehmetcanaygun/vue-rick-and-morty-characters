<template>
  <ul class="character-list">
    <CharacterItem
      :key="character.id"
      v-for="character in characters"
      :character="character"
    />
  </ul>
</template>

<script>
import CharacterItem from "./CharacterItem.vue";

export default {
  name: "CharacterList",
  props: {
    characters: Array,
  },
  components: {
    CharacterItem,
  },
};
</script>

<style lang="scss" scoped>
// Imports
@import "../styles/variables";

.character-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 30px;
}

// Media Queries
@media (max-width: 768px) {
  .character-list {
    grid-template-columns: 1fr;
  }
}
</style>