<template>
  <div class="container">
    <div>
      <h1 class="text-4xl font-semibold text-gray-800 mb-8">
        The main index page
      </h1>
      <div class="flex">
        <ul class="w-64 px-2 text-gray-600">
          <li v-for="character in characters.results" :key="character.id">
            <n-link
              :to="character.id"
              class="hover:font-bold hover:text-gray-900 leading-loose"
              >{{ character.name }}</n-link
            >
          </li>
        </ul>
        <div class="flex-grow bg-white min-h-full">
          <n-child :key="$route.params.id"></n-child>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'Character',
  fetch({ redirect, route }) {
    if (!route.params.id) {
      redirect('/1')
    }
  },
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
