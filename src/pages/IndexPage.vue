<template>
  <q-page>
   <!--<h3>hello world</h3>-->

   <div class="q-pa-md">
    <q-img
      src="images/homepic.jpeg"
      class="q-responsive"
      style="max-height: 500px;"
      alt="Sample Image"
    />
  </div>

   <div class="container q-pa-md row items-start q-gutter-lg">
   <q-list v-for="article in articles" :key="article.id">
    <q-item>
      <q-item-section>
        <q-card class="my-card q-pa-md cursor-pointer" clickable @click="goToArticle(article.id)">
          <div>
          <img :src="article.image" :alt="article.title" style="width: 100%; height: 200px">
          </div>

          <q-card-section>
            <div class="text" style="width: fit-content;">{{ article.title }}</div>
          </q-card-section>

        </q-card>
      </q-item-section>
    </q-item>
   </q-list>
   </div>
  </q-page>
</template>

<script>
  import {articles} from "../assets/data.js"

  export default {
    data() {
      return {
        articles
      }
    },

    methods: {
      goToArticle(id) {
        this.$router.push(`/article/${id}`);
      },
    }
    
  }

</script>


<style scoped>

  .container {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .my-card {
  width: 400px;
  transition: transform 0.3s ease;
  }

  .my-card:hover {
  transform: scale(1.1); /* Increase size by 10% on hover */
}

  .text {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: large;
    font-weight: 300;
    text-align: center;
  }

  @media (max-width: 500px) {
    .my-card {
      width: 350px;
    }
  }

 


 
  
</style>
