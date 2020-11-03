<template>
  <div>
    <h1>Comments page with slug parameter :</h1>
    <p>{{ $route.params.slug }}</p>
  </div>
</template>

<script>
export default {
  name: 'Comments',
  validate({ params }) {
    return /^\d+$/.test(params.slug)
  },
}
</script>

<style scoped></style>
