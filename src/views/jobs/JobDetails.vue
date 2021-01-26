<template>
  <h1>Job Details Page</h1>
  <div v-if="loaded">
    <p>The job title is {{ job.title }}</p>
    <p>The job id is {{ job.id }}</p>
    <p>Description: {{ job.details }}</p>
  </div>
</template>

<script>
export default {
  props: ['id'],
  data() {
    return {
      job: null,
      loaded: false
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs/' + this.id)
      .then(response => response.json())
      .then(data => {
        this.job = data
        this.loaded = true
      })
      .catch(error => console.log(error.message))
  }
}
</script>

<style lang="scss" scoped></style>
