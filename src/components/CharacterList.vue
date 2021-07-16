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
ul {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
</style>