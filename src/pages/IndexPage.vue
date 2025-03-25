<template>
  <q-page>
    <div class="q-pa-md">
      <q-img
        src="images/homepic.jpeg"
        class="q-responsive"
        style="max-height: 500px"
        alt="Sample Image"
      />
    </div>

    <div class="container q-pa-md row justify-center q-gutter-lg">
      <q-list v-for="article in articles" :key="article.id">
        <q-item>
          <q-item-section>
            <q-card
              class="my-card cursor-pointer"
              clickable
              @click="goToArticle(article.id)"
            >
              <q-img
                :src="article.image"
                :alt="article.title"
                class="card-image"
              />
              <q-card-section class="card-content">
                <div class="text">{{ article.title }}</div>
              </q-card-section>
            </q-card>
          </q-item-section>
        </q-item>
      </q-list>
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
/* Flex container to align cards properly */
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 16px;
}

/* Ensure all cards have the same size */
.my-card {
  width: 350px;
  height: 400px; /* Fixed height */
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease;
}

.my-card:hover {
  transform: scale(1.05);
}

/* Ensure all images inside cards have the same size */
.card-image {
  width: 100%;
  height: 250px; /* Fixed height */
  object-fit: cover; /* Prevents distortion */
}

/* Card content section with uniform spacing */
.card-content {
  flex-grow: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

/* Title text styling */
.text {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: large;
  font-weight: 300;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .my-card {
    width: 300px;
    height: 370px;
  }

  .card-image {
    height: 220px;
  }
}

@media (max-width: 500px) {
  .my-card {
    width: 280px;
    height: 350px;
  }

  .card-image {
    height: 200px;
  }
}
</style>
