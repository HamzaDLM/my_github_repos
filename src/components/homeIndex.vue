<script>

export default {
  name: 'homeIndex',
  props: {
    msg: String
  },
  data() {
    return {
      data: [
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        {
          title: "github_repo_name",
          description: "This small python app takes in an excel file with data and a corresponding word document template and mass generate files",
          date: "01/30/2022",
          language: "Python"
        },
        
      ]
    } 
  }
}

</script>

<template>
  <div>
    <div class="container top-container d-flex justify-content-center">
      <div class="row mt-5">
        <div class="col-3">
          <img src="https://avatars.githubusercontent.com/HamzaDLM" 
            class="rounded-circle user-avatar mb-3"
            style="width: 100px;"
            alt="Avatar"
          />
        </div>
        <div class="col-9">
          <h1 class="title mt-2">My Github Repos</h1>
          <p class="text-muted user-name ">@HamzaDLM</p>
        </div>
      </div>
    </div>

    <div class="container mid-container">
      <div class="row mt-2 scolling">
        <div v-for="(item, index) in data" :key="index" class="col-3">
          <div class="card repo-card m-4" style="width: 18rem; height: 14rem;">
            <div class="card-body">
              <p class="card-title">{{ item.title }}</p>
              <p class="card-text">{{ item.description }}</p>
              <div class="row">
                <div class="col-6">
                  <p class="time"><span class="badge rounded-pill text-bg-secondary">.</span> {{ item.date }}</p>
                </div>
                <div class="col-6">
                  <span class="badge rounded-pill text-bg-primary">Python</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>


