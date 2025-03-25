<template>
  <q-page class="flex flex-center">
    <div class="container">
      <!-- Back Button -->
      <q-btn
        icon="arrow_back"
        label="Back to Articles"
        flat
        class="back-button"
        @click="goBack"
      />

      <q-card class="my-card" flat bordered>
        <!-- Article Image -->
        <q-card-section class="image-container">
          <q-img :src="article.image" class="article-image" />
        </q-card-section>

        <!-- Article Title -->
        <q-card-section class="title-section">
          <div class="text-h5">{{ article.title }}</div>
        </q-card-section>

        <!-- Article Content -->
        <q-card-section class="content-section">
          <p v-html="article.content"></p>
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
      this.$router.push("/"); // Navigates back to IndexPage.vue
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 1300px;
  width: 100%;
  padding: 20px;
}

.back-button {
  margin-bottom: 15px;
  font-size: larger;
}

.my-card {
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  background-color: #fff;
}

.image-container {
  text-align: center;
  padding: 15px;
}

.article-image {
  max-width: 90%;
  height: auto;
  border-radius: 10px;
}

.title-section {
  text-align: center;
  background-color: #e6c8a5;
  padding: 15px;
  font-weight: bold;
}

.content-section {
  text-align: justify;
  padding: 25px;
  border: 1px solid grey;
  margin: 15px;
  border-radius: 15px;
  background-color: #faf5f0;
  font-size: 18px;
}

/* Responsive Design */
@media (max-width: 600px) {
  .container {
    padding: 10px;
  }

  .content-section {
    padding: 15px;
    font-size: 16px;
  }

  .back-button {
    width: 100%;
    text-align: center;
  }
}
</style>
