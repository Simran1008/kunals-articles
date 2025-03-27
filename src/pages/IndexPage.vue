<template>
  <q-page class="q-pa-md">
    <!-- Hero Section -->
    <div class="hero-container">
      <!-- Text Content -->
      <div class="hero-text">
        <h1>Kunal Nadkarni</h1>
        <p class="subtitle">
          LLM, Comparative and International Dispute Resolution, Queen Mary
          University of London
        </p>
        <p class="subtitle">BA LLB, Symbiosis Law School, Hyderabad</p>
      </div>

      <!-- Hero Image -->
      <q-img
        src="images/header-pic.jpg"
        class="hero-image"
        alt="Profile Image"
      />
    </div>

    <!-- Search Bar -->
    <div class="search-container q-mb-lg">
      <q-input
        v-model="searchQuery"
        filled
        debounce="300"
        placeholder="Search articles..."
        clearable
        class="search-bar"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
    </div>

    <!-- Article Cards -->
    <div class="articles-container row justify-center q-gutter-md">
      <q-card
        v-for="article in filteredArticles"
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
      searchQuery: "",
    };
  },
  computed: {
    filteredArticles() {
      return this.articles.filter((article) =>
        article.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    goToArticle(id) {
      this.$router.push(`/article/${id}`);
    },
  },
};
</script>

<style scoped>
/* Hero Section */
.hero-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  margin-bottom: 30px;
  padding: 30px;
  border-radius: 12px;
  background: linear-gradient(
    135deg,
    #f9e7d2,
    #eed9c4
  ); /* Softer & more visible gradient */
  color: #4b382a;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  border: 2px solid #d8b999;
}

/* Text Section */
.hero-text {
  width: 50%;
  padding: 20px;
}

.hero-text h1 {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 10px;
  font-family: "Poppins", sans-serif;
  color: black;
}

.subtitle {
  font-size: 1.1rem;
  font-weight: 400;
  opacity: 0.9;
  color: black;
}

/* Image Section */
.hero-image {
  width: 50%;
  max-height: 500px; /* Increased height */
  border-radius: 12px;
  object-fit: cover;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

/* Search Bar */
.search-container {
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 600px;
  margin: 0 auto 40px;
}

.search-bar {
  width: 100%;
  height: 50px;
  font-size: 1.1rem;
}

/* Article Cards */
.articles-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

/* Card Styling */
.article-card {
  width: 320px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  background: white;
  border: 1px solid #d8b999;
}

.article-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
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
  font-size: 1.2rem;
  font-weight: 600;
  color: #3f2e21;
  font-family: "Poppins", sans-serif;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-container {
    flex-direction: column;
    text-align: center;
    padding: 20px;
  }

  .hero-text,
  .hero-image {
    width: 100%;
  }

  .hero-image {
    max-height: 300px;
  }
}

@media (max-width: 500px) {
  .article-card {
    width: 260px;
  }

  .hero-image {
    max-height: 250px;
  }
}
</style>
