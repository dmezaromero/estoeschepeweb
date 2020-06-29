<template>
  <div class="container">
    <div class="uk-position-relative uk-background-muted" uk-height-viewport="offset-top: true; min-height: 600">
      <div class="uk-position-center">
        <div class="uk-width-1-2@m uk-text-center uk-margin-auto">
          <h1>{{ home.data.homepage.title}}</h1>
          <p>{{ home.data.homepage.description}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  components: {},
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
    return { home: data };
  }
};
</script>
