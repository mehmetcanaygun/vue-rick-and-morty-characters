<template>
  <main class="home-page">
    <CharacterList :characters="characters" />
  </main>
</template>

<script>
import CharacterList from "../components/CharacterList.vue";

export default {
  name: "Home",
  components: {
    CharacterList,
  },
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async getCharacters() {
      const res = await fetch("https://rickandmortyapi.com/api/character");

      const data = await res.json();

      return data.results;
    },
  },
  async created() {
    this.characters = await this.getCharacters();
    console.log(this.characters);
  },
};
</script>
