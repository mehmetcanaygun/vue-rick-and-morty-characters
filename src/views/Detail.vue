<template>
  <main class="detail-page">
    <router-link
      to="/"
      class="back-link"
    ><i class="fas fa-chevron-left"></i> Go Back</router-link>

    <h1 className="detail-title">
      Details for <span>{{character.name}}</span>
    </h1>

    <div class="character-container">
      <!-- Character Image -->
      <div className="img-container">
        <div
          className="img"
          :style="{ backgroundImage: `url(${character.image})` }"
        ></div>
      </div>
      <!-- Character Info -->
      <div className="info">
        <ul className="detail-list">
          <li>
            <span>Species:</span> {{character.species}}
          </li>
          <li>
            <span>Gender:</span> {{character.gender}}
          </li>
          <li>
            <span>Status:</span> {{character.status}}
          </li>
          <li>
            <span>Location:</span> {{character.location.name}}
          </li>
          <li>
            <span>Origin:</span> {{character.origin.name}}
          </li>
          <!-- <li>
            <span>Last Episodes:</span>
            <ul className="episodes-list">
              {characterEpisodes &&
                characterEpisodes
                  .slice()
                  .reverse()
                  .map((ep) => (
                    <li key={ep.id}>
                      &#8212; <b>{ep.episode}</b>. {ep.name} ({ep.air_date})
                    </li>
                  ))}
            </ul>
          </li> -->
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Detail",
  data() {
    return {
      character: null,
    };
  },
  methods: {
    async getCharacter(id) {
      const res = await fetch(
        `https://rickandmortyapi.com/api/character/${id}`
      );

      const data = await res.json();

      return data;
    },
  },
  async created() {
    this.character = await this.getCharacter(this.$route.params.id);
  },
};
</script>

<style lang="scss" scoped>
// Imports
@import "../styles/variables";

.detail-page {
  padding: 0 $px;

  .detail-title {
    margin: 30px 0;

    span {
      color: $color-secondary;
    }
  }
}

.character-container {
  margin: 30px 0;
  display: grid;
  grid-template-columns: 2fr 3fr;
  gap: 3vw;

  .img-container {
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.3);
    align-self: start;

    .img {
      width: 100%;
      height: 400px;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      background-attachment: scroll;
      transition: transform 0.5s;
    }
  }

  .img-container:hover .img {
    transform: scale(1.1);
  }

  .info {
    .detail-list > li {
      font-size: 22px;
      padding: 10px 6px;

      span {
        font-weight: bold;
        color: $color-secondary;
      }

      &:nth-child(even) {
        background-color: rgba($color-primary, 0.3);
      }

      .episodes-list {
        margin-top: 10px;

        li {
          font-size: 18px;
        }
      }
    }
  }
}

.back-link {
  display: inline-block;
  width: 150px;
  height: 40px;
  margin-bottom: 30px;
  border-radius: 6px;
  background-color: $color-light;
  color: $color-primary;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 14px;
  text-transform: uppercase;
  font-weight: bold;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.2);

  i {
    margin-right: 10px;
  }
}

// Media Queries
@media (max-width: 768px) {
  // Character Detail Page
  .detail-page {
    padding: 0 $px-sm;

    .detail-title {
      font-size: 24px;
    }
  }

  .character-container {
    grid-template-columns: 1fr;
    gap: 3vw;

    .img-container .img {
      height: 50vw;
    }

    .info {
      .detail-list li {
        font-size: 16px;
        padding: 8px 0;

        .episodes-list {
          margin-top: 0px;

          li {
            font-size: 14px;
            padding: 4px;
          }
        }
      }
    }
  }
}
</style>