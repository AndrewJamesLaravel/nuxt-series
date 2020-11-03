<template>
  <div class="container">
    <div>
      <h1 class="text-4 font-semibold text-gray-800 mb-8">
        The main index page
      </h1>
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
