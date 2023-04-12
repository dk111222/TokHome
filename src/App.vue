<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        <a class="navbar-brand" href="#">Toc Inc. 官网</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div
          class="collapse navbar-collapse justify-content-end"
          id="navbarNav"
        >
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">首页</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">关于我们</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">联系我们</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="container py-5">
      <div class="row">
        <div class="col-md-4" v-for="(app, index) in apps" :key="index">
          <div class="card mb-3">
            <img :src="app.image" class="card-img-top" alt="App Image" />
            <div class="card-body">
              <h5 class="card-title">{{ app.title }}</h5>
              <p class="card-text">{{ app.description }}</p>
              <a :href="app.downloadUrl" class="btn btn-primary">下载</a>
              <a :href="app.googlePlayUrl" class="btn btn-outline-primary"
                >Google Play</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>

    <footer class="bg-light text-center text-lg-start">
      <div class="text-center p-3">© 2023 Toc Inc. 官网</div>
    </footer>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      apps: [],
    };
  },
  created() {
    axios.get("/apps.json").then((response) => {
      this.apps = response.data;
    });
  },
};
</script>