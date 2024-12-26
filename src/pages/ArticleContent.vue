<template>
  <q-page>
    <div class="container">

      <q-card class="my-card" flat>
        <q-card-section style="text-align: center;">
          <img :src="article.image">
        </q-card-section>

        <q-card-section style="text-align: center; background-color: #e6c8a5;">
          <div class="text-h6" style="font-weight: bold;">{{ article.title }}</div>
        </q-card-section>

        <q-card-section class="q-pt-none" style="text-align: justify; padding: 30px; border: 1px solid grey; margin-top: 20px; border-radius: 30px;">
          <p v-html="article.content"></p>
        </q-card-section>
      </q-card>

    </div>
  </q-page>
</template>

<script>
import {articles} from "../assets/data.js";

export default {
  name: "ArticleContent",
  props: ['id'],
  computed: {
    article() {
      return articles.find((article) => article.id == this.id);
    },
  },
};
</script>

<style scoped>
.container {
  padding: 50px;
}

img {
  max-width: 100%;
  height: auto;
}

* {
  font-family: 'Times New Roman', Times, serif;
  font-size: 20px;
  font-weight: lighter;
}

@media (max-width: 500px) {
  p {
    font-size: small;
  }
}

</style>
