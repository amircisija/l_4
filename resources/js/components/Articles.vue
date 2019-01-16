<template>
  <div>
    <h2>Test Module</h2>
    <div class="row">
      <div class="card-columns">
        <div class="card text-left" v-for="article in articles" :key="article.id">
          <div class="card-body">
            <h4 class="card-title">{{ article.title }}</h4>
            <p class="card-text">{{ article.body }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      articles: [],
      article: {
        id: "",
        title: "",
        body: ""
      },
      article_id: "",
      edit: false
    };
  },
  created() {
    this.fetchArticles();
  },
  methods: {
    fetchArticles() {
      fetch("api/articles")
        .then(res => res.json())
        .then(res => {
          this.articles = res.data;
        });
    }
  }
};
</script>