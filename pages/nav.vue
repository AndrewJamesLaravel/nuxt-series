<template>
  <div>
    <ul>
      <li>
        <n-link to="/nav/about">About</n-link>
        <n-link to="/nav/contact">Contact</n-link>
      </li>
    </ul>
    <div class="bg-gray-500">
      <n-child />
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavVue',
}
</script>

<style scoped></style>
