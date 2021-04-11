<template>
  <div class="home">
    <JobList />
  </div>
</template>

<script>
// @ is an alias to /src
import JobList from '../components/JobList'

export default {
  name: 'Home',
  components: {
    JobList,
  }
}
</script>
