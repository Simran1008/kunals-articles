<template>
  <q-page class="q-pa-md">
    <!-- Hero Image -->
    <div class="hero-container">
      <q-img src="images/homepic.jpeg" class="hero-image" alt="Sample Image" />
    </div>

    <!-- Article Cards -->
    <div class="articles-container row justify-center q-gutter-md">
      <q-card
        v-for="article in articles"
        :key="article.id"
        class="article-card cursor-pointer"
        clickable
        @click="goToArticle(article.id)"
      >
        <q-img
          :src="article.image"
          :alt="article.title"
          class="article-image"
        />
        <q-card-section class="article-content">
          <div class="article-title">{{ article.title }}</div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { articles } from "../assets/data.js";

export default {
  data() {
    return {
      articles,
    };
  },
  methods: {
    goToArticle(id) {
      this.$router.push(`/article/${id}`);
    },
  },
};
</script>

<style scoped>
/* Hero Image Section */
.hero-container {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
}

.hero-image {
  width: 100%;
  max-height: 450px;
  border-radius: 12px;
  object-fit: cover;
}

/* Article Cards */
.articles-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

/* Card Styling */
.article-card {
  width: 320px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  background: #ffffff;
}

.article-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

/* Image Styling */
.article-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

/* Article Content */
.article-content {
  padding: 15px;
  text-align: center;
}

.article-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #333;
  font-family: "Poppins", sans-serif;
}

/* Responsive Design */
@media (max-width: 768px) {
  .article-card {
    width: 280px;
  }

  .hero-image {
    max-height: 350px;
  }
}

@media (max-width: 500px) {
  .article-card {
    width: 260px;
  }

  .hero-image {
    max-height: 280px;
  }
}
</style>
