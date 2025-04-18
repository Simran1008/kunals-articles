<template>
  <q-page class="flex flex-center">
    <div class="container">
      <!-- Back Button -->
      <q-btn
        icon="arrow_back"
        label="Back to Articles"
        class="back-button"
        unelevated
        @click="goBack"
      />

      <q-card class="article-card">
        <!-- Article Image -->
        <q-img :src="article.image" class="article-image" />

        <!-- Article Content -->
        <q-card-section class="article-content">
          <div class="article-title">{{ article.title }}</div>
          <div class="article-text" v-html="article.content"></div>
          <div class="article-footnotes" v-html="article.footnotes"></div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { articles } from "../assets/data.js";

export default {
  name: "ArticleContent",
  props: ["id"],
  computed: {
    article() {
      return articles.find((article) => article.id == this.id);
    },
  },
  methods: {
    goBack() {
      this.$router.push("/"); // Navigates back to the home page
    },
  },
};
</script>

<style scoped>
/* Page Container */
.container {
  max-width: 1300px;
  width: 100%;
  padding: 20px;
}

/* Back Button */
.back-button {
  margin-bottom: 20px;
  font-size: 16px;
  font-weight: 500;
  border-radius: 8px;
}

/* Card Styling */
.article-card {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  transition: 0.3s ease;
}

.article-card:hover {
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

/* Image */
.article-image {
  width: 100%;
  height: 350px;
  object-fit: cover;
}

/* Content */
.article-content {
  padding: 25px;
}

.article-title {
  font-size: 1.5rem;
  font-weight: 500;
  text-align: center;
  margin-bottom: 15px;
  color: #333;
  font-family: "Poppins", sans-serif;
}

.article-text {
  font-size: 18px;
  line-height: 1.6;
  text-align: justify;
  background-color: #faf5f0;
  padding: 20px;
  border-radius: 8px;
}

.article-footnotes {
  margin-top: 30px;
  padding: 20px;
  background-color: #f4f4f4; /* Purple accent for style */
  border-radius: 8px;
  font-size: 14px;
  line-height: 1.7;
  color: #555;
  font-family: "Georgia", serif;
}

.article-footnotes sup {
  font-weight: bold;
  font-size: 12px;
  vertical-align: top;
  margin-right: 4px;
}

/* Responsive Design */
@media (max-width: 600px) {
  .container {
    padding: 15px;
  }

  .article-image {
    height: 250px;
  }

  .article-title {
    font-size: 1.3rem;
  }

  .article-text {
    font-size: 16px;
    padding: 15px;
  }

  .back-button {
    width: 100%;
  }
}
</style>
