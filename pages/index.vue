<template>
  <div>
    <div class="container uk-position-relative">
      <div class="uk-position-center">
        <div class="heading uk-width-1-2@m uk-text-center uk-margin-auto uk-light">
          <h1>{{ home.data.homepage.title}}</h1>
          <p>{{ home.data.homepage.description}}</p>
          <a href="https://www.instagram.com/estoeschepe/" class="uk-button uk-button-primary" target="_blank">Ver Más</a>
        </div>
      </div>
      <backgroundimages v-bind:images="home.data.homepage.background_images"></backgroundimages>
      <svg class="cursor" width="80" height="80" viewBox="0 0 80 80">
			  <circle class="cursor__inner" cx="40" cy="40" r="20"/>
		  </svg>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import backgroundimages from "~/components/background-images";

export default {
  components: {
    backgroundimages
  },
  async asyncData() {
    const { data } = await axios.post(
      "https://api-us-east-1.graphcms.com/v2/ck8xhe6lm1tn201xp4dbaf2sb/master",
      {
        query: `{  homepage(where: {id: "ckbzq85dc19kz0176if88p2jt"}, stage: PUBLISHED) {
                    id
                    title
                    description
                    background_images(first: 100) {
                      id
                      handle
                      fileName
                      height
                      url
                    }
                  }
                }`
      }
    );
    return { 
      home: data
    };
  },
  head() {
    return {
      bodyAttrs: {
        class: 'home',
      }
    }
  }
    
};
</script>