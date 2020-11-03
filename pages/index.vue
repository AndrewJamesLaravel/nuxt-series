<template>
  <div class="container">
    <div>
      <h1 class="text-4 font-semibold text-gray-800 mb-8">
        The main index page
      </h1>
      <button
        class="bg-gray-700 p-4 border text-white"
        @click="characterId = characterId + 1"
      >
        Next character
      </button>
      <button
        class="bg-yellow-700 p-4 border text-white"
        @click="characterId = characterId - 1"
      >
        Previous character
      </button>
      <h3 class="text-2xl">{{ character.name }} id: {{ character.id }}</h3>
      <ul>
        <li v-for="character in characters.results" :key="character.id">
          {{ character.name }}
          {{ character.status }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      characterId: 1,
    }
  },
  apollo: {
    characters: gql`
      query getCharacters {
        characters {
          results {
            id
            name
            status
          }
        }
      }
    `,
    character: {
      query: gql`
        query getCharacter($id: ID!) {
          character(id: $id) {
            id
            name
          }
        }
      `,
      variables() {
        return {
          id: this.characterId,
        }
      },
    },
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
