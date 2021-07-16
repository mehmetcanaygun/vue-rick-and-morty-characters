<template>
  <main class="home-page">
    <ThePagination
      :pagination="pagination"
      @get-page="getPage"
    />
    <CharacterList :characters="characters" />
    <ThePagination
      :pagination="pagination"
      @get-page="getPage"
    />
  </main>
</template>

<script>
import CharacterList from "../components/CharacterList";
import ThePagination from "../components/ThePagination";

export default {
  name: "Home",
  components: {
    CharacterList,
    ThePagination,
  },
  data() {
    return {
      characters: [],
      pagination: null,
    };
  },
  methods: {
    async getCharacters() {
      const res = await fetch("https://rickandmortyapi.com/api/character");

      const data = await res.json();

      return [data.results, data.info];
    },
    async getPage(pageUrl) {
      const res = await fetch(pageUrl);

      const data = await res.json();

      [this.characters, this.pagination] = [data.results, data.info];
    },
  },
  async created() {
    [this.characters, this.pagination] = await this.getCharacters();
  },
};
</script>
