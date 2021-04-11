<template>
  <div>
    <div class="filter">
      <input
        type="text"
        v-model="search"
        class="input"
        placeholder="Filter by title..."
      />
    </div>
    <div class="card-group grid">
      <div class="card" v-for="job in filteredJobs" :key="job.id">
        <router-link
          :to="{
            name: 'JobDetails',
            params: {
              id: job.id,
              title: job.title,
              type: job.type,
              company: job.company,
              company_url: job.company_url,
              created_at: job.created_at,
              location: job.location,
              description: job.description,
              logo: job.company_logo,
            },
          }"
        >
          <img
            :src="job.company_logo"
            class="card-img-top"
            alt="company logo"
          />

          <div class="card-body px-4">
            
            <p class="card-text">
              <small class="text-muted">
                {{ job.created_at }} - {{ job.type }}</small
              >
            </p>

            <h5 class="card-title">{{ job.title }}</h5>
            <p class="card-text">
              <small class="text-muted">{{ job.company }} </small>
            </p>
            <h6 class="location pt-2">{{ job.location }}</h6>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      jobs: [],
      search: "",
    };
  },
  mounted() {
    axios
      .get("https://cors.bridged.cc/https://jobs.github.com/positions.json")
      .then((response) => (this.jobs = response.data))
      .catch((err) => console.log(err.message));
  },
  computed: {
    filteredJobs: function () {
      return this.jobs.filter((job) => {
        return job.title.toLowerCase().match(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
  color: black;
}

.card-group {
  justify-content: center;
  align-items: center;
  margin-top: 80px;
  display: grid;
  grid-template-rows: 1fr;
  grid-template-columns: 1fr;
}
.card {
  height: 253px;
  width: 327px;
  position: relative;
  background-color: white;
  border: none;
  border-radius: 10px;
  margin-bottom: 100px;
  justify-content: center;
  align-items: center;
  justify-self: center;
}

.card .card-img-top {
  width: 50px;
  height: 50px;
  object-fit: contain;
  position: absolute;
  top: -25px;
  left: 32px;
  border-radius: 15px;
}

.location {
  color: #5964e0;
  font-weight: bold;
}

.filter {
  display: flex;
  justify-content: center;
}

.input {
  position: relative;
  display: flex;
}

.input {
  height: 80px;
  width: 327px;
  border: none;
  position: absolute;
  top: 95px;
  border-radius: 15px;
  padding-left: 20px;
}

@media (min-width: 700px) {
  .card-group {
    display: grid;
    grid-template-rows: 253px;
    grid-template-columns: 339px 339px;
    align-items: center;
    margin-top: 110px;
  }

  .card {
    height: 253px;
    width: 327px;
    position: relative;
    background-color: white;
    border: none;
    border-radius: 10px;
  }

  .card .card-img-top {
    width: 50px;
    height: 50px;
    object-fit: contain;
    position: absolute;
    top: -25px;
    left: 32px;
    border-radius: 15px;
  }

  .input {
    height: 80px;
    width: 670px;
    border: none;
    position: absolute;
    top: 95px;
    border-radius: 15px;
    padding-left: 20px;
  }
}

@media (min-width: 1000px) {
  .card-group {
    display: grid;
    grid-template-rows: 253px;
    grid-template-columns: 350px 350px 350px;
    align-items: center;
    margin-top: 110px;
  }

  .card {
    height: 253px;
    width: 327px;
    position: relative;
    background-color: white;
    border: none;
    border-radius: 10px;
  }

  .card .card-img-top {
    width: 50px;
    height: 50px;
    object-fit: contain;
    position: absolute;
    top: -25px;
    left: 32px;
    border-radius: 15px;
  }

  .input {
    height: 80px;
    width: 73%;
    border: none;
    position: absolute;
    top: 95px;
    border-radius: 15px;
    padding-left: 20px;
  }
}
</style>
