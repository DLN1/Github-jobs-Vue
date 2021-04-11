<template>
<div>
    <div class="card companyCard">
        <img 
        :src="$route.params.logo"
        alt="company Logo"
        class="company-logo"/>
  <h5>{{ $route.params.company }}</h5>
  <p class="card-text"><small class="text-muted">{{ $route.params.company_url }}</small></p>
  <a :href="$route.params.company_url" target="_blank">Company Site</a>
  </div>
  <div class="description card mt-5 p-5">
      <p class="card-text"><small class="text-muted">{{ $route.params.created_at}} - {{ $route.params.type }}</small></p>
      <h5 class="text-center">{{ $route.params.title }}</h5>
      <h6 class="location pt-2">{{ $route.params.location}}</h6>
      <a class="btn btn-primary mt-4 mb-5">Apply Now</a>

      <p class="card-text"><small class="text-muted">
          {{ $route.params.description }}
          </small></p>
  </div>
</div>
</template>

<script>

export default {
 
}

</script>

<style scoped>
    .companyCard {
        width: 80%;
        margin: -20px auto;
        height: 230px;
        padding: 50px;
        justify-content: center;
        align-items: center;
        display: flex;
    }

    .company-logo {
        position: absolute;
        top: -25px;
        height: 50px;
        width: 50px;
    }

    .companyCard a {
        width: 147px;
        height: 48px;
        padding: 10px;
        border: none;
        color: #5964E0;
        background-color: #eeeded;
        font-weight: 600;
        text-decoration: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    .location {
  color: #5964e0;
  font-weight: bold;
}

.description {
    width: 80%;
    margin: auto;
}
</style>