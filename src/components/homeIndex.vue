<script>
import axios from "axios"
import moment from 'moment'

export default {
  name: 'homeIndex',
  props: {
    msg: String
  },
  data() {
    return {
      items: [],
      githubUser: "HamzaDLM",
      avatarURL: "https://avatars.githubusercontent.com/HamzaDLM"
    } 
  },
  created() {
    this.getRepos()
  },
  methods: {
    formatDate(param) {
      return moment(param).format("MMM Do YY")
    },
    pillsColor(language) {
      switch (language) {
        case "Python": return "blue"
        case "Vue": return "lightgreen"
        case "Javascript": return "yellow"
        default: return "var(--primary)"
      }
    },
    sorted(param) {
      param.sort(function (a, b) {
        return new Date(b.updated_at) - new Date(a.updated_at);
      })
    },
    getAvatar() {
      this.avatarURL = "https://avatars.githubusercontent.com/" + this.githubUser
    } ,
    async getRepos() {
      return await axios.create({baseURL: "https://api.github.com/users/" + this.githubUser + "/repos"})
        .get()
        .then((response) => {
            this.items = response.data
            this.items = this.items.sort((a, b) => new Date(b.updated_at) - new Date(a.updated_at))
            this.getAvatar()
          })
        .catch((error) => {
          console.log(error);
        })
    }
  }
}

</script>

<template>
  <div>
    <div class="container top-container d-flex justify-content-center">
      <div class="row mt-5">
        <div class="col-3">
          <img :src="avatarURL"  
            class="rounded-circle user-avatar mb-3"
            style="width: 100px;"
            alt="Avatar"
          />
        </div>
        <div class="col-9">
          <h1 class="title mt-2">My Github Repos</h1>
          <!-- <p class="text-muted user-name ">@HamzaDLM</p>
           -->
          <div class="d-flex">
            <input
                type="search"
                class="form-control search rounded"
                placeholder="Type your github username"
                aria-label="Search"
                aria-describedby="search-addon"
                v-model="githubUser"
            >
            <a href="#" @click="getRepos()"><i class="fas m-2 fa-search" /></a>
          </div>
        </div>
      </div>
    </div>

    <div class="container mid-container">
      <div class="row mt-3 scroll">
        <div v-for="(item, index) in items" :key="index" class="col col-sm-3 col-md-6 col-lg-3">
          <div class="card repo-card m-2" style="width: 18rem; height: 14rem;">
            <div class="card-body">
              <p class="card-title">{{ item.name }}</p>
              <p class="card-text">{{ item.description }}</p>
              <div class="row" style="position:absolute; bottom:0;">
                <div class="col">
                  <p class="time">
                    <span class="badge rounded-pill text-bg-secondary">
                      <i class="fa-regular fa-timer"></i>
                    </span> {{ formatDate(item.updated_at) }}
                  </p>
                </div>
                <div class="col">
                  <span class="badge rounded-pill lang text-bg-primary">{{ item.language }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <footer class="text-center text-muted fixed-bottom">
      <div class="text-center p-3">
        <p class="m-0"> Copyright free ♥ <span>
          <a href="https://github.com/HamzaDLM" target="_blank">Developer's Github</a>
        </span></p>
      </div>
    </footer>
    
  </div>
</template>


