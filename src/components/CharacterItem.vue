<template>
  <li class="character-item">
    <router-link :to="{ name: 'Detail', params: { id: character.id }}">
      <div class="img-container">
        <h3>{{character.name}}</h3>
        <div
          class="img"
          :style="{ backgroundImage: 'url(' + character.image + ')' }"
        ></div>
      </div>
      <div class="info-container">
        <p>
          <strong>Gender:</strong> {{character.gender}}
        </p>
        <p>
          <strong>Species:</strong> {{character.species}}
        </p>
        <p>
          <strong>Status:</strong> {{character.status}}
        </p>
        <p>
          <strong>Location:</strong> {{character.location.name}}
        </p>

        <div class="logo-container">
          <img
            src="@/assets/logo.png"
            alt="Rick and Morty logo"
          />
        </div>
      </div>
    </router-link>
  </li>
</template>

<script>
export default {
  name: "CharacterItem",
  props: {
    character: Object,
  },
};
</script>

<style lang="scss" scoped>
// Imports
@import "../styles/variables";

.character-item {
  box-shadow: 0px 5px 25px rgba(0, 0, 0, 0.3);
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s;

  a {
    display: grid;
    grid-template-columns: 2fr 3fr;
    width: 100%;
    height: 100%;
    text-decoration: none;
    color: #000;
    transition: color 0.2s;
  }

  .img-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px 10px;
    background-image: linear-gradient(
      $color-primary,
      darken($color-primary, 10)
    );
    border-radius: 12px 0px 0px 12px;

    h3 {
      margin-bottom: 20px;
      color: $color-secondary;
      text-align: center;
    }

    .img {
      width: 160px;
      height: 160px;
      border-radius: 50%;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.7);
      background-size: cover;
      background-position: center;
    }
  }

  .info-container {
    width: 100%;
    padding: 20px 10px 10px 20px;
    position: relative;

    p {
      margin-bottom: 10px;
      font-size: 16px;

      strong {
        color: brown;
      }
    }
  }

  .logo-container {
    width: 200px;
    position: absolute;
    bottom: -20px;
    right: -8px;
    z-index: -1;

    img {
      max-width: 100%;
      background-size: cover;
      background-position: center;
    }
  }
}

.character-item:hover {
  transform: scale(1.02);
}

// Media Queries
@media (max-width: 1024px) {
  .character-item {
    .img-container .img {
      width: 100px;
      height: 100px;
    }
  }
}

@media (max-width: 768px) {
  .character-item {
    .img-container h3 {
      font-size: 16px;
    }

    .info-container p {
      font-size: 14px;
    }
  }
}
</style>