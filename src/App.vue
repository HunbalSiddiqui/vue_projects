<script>
export default {
        data: () => ({
          newCharacter: {
            name: ''
          },
          characterList: [
            {
              name: 'Aang'
            },
            {
              name: 'Zuko'
            },
            {
              name: 'Toph'
            },
            {
              name: 'Katara'
            }
          ],
          favoriteList: []
        }),
        methods: {
          addNewCharacter() {
            this.characterList.push(this.newCharacter)
            this.newCharacter = { name: '' }
          },
          favoriteCharacter(character) {
            this.favoriteList.push(character)
          }
        }
      }
</script>

<template>
 <div>
      <p v-if="characterList.length === 0">There are no characters</p>
      <ul>
        <li v-for="character in characterList">
          <p>{{ character.name }}</p>
          <button @click="favoriteCharacter(character)">⭐ Favorite</button>
        </li>
      </ul>
      <h2>Favorite Characters</h2>
      <ul v-if="favoriteList.length > 0">
        <li v-for="character in favoriteList">{{ character }}</li>
      </ul>
      <p v-else>No favorite characters yet!</p>
      <h2>New Character</h2>
      <pre>{{ newCharacter }}</pre>
      <label for="character-name">Name</label>
      <input
        type="text"
        v-model="newCharacter.name"
        @keyup.enter="addNewCharacter"
      />
      <p>
        <span v-for="(character, index) in characterList"
          >{{ character.name }}{{ index === characterList.length - 1 ? '' : ', '
          }}
        </span>
      </p>
    </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
