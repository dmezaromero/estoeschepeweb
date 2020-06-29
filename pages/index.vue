<template>
  <div>
    <div class="container uk-position-relative">
      <div class="uk-position-center">
        <div class="heading uk-width-1-2@m uk-text-center uk-margin-auto uk-light">
          <h1>{{ home.data.homepage.title}}</h1>
          <p>{{ home.data.homepage.description}}</p>
          <nuxt-link to="https://www.instagram.com/estoeschepe/" class="uk-button uk-button-primary">Ver Más</nuxt-link>
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
<style>
html, 
body, 
main {
	height: 100%;
	width: 100%;
	position: relative;
	overflow: hidden;
}

body {
	margin: 0;
	--color-text: #d05400;
    --color-bg: #0c0c0c;
    --color-link: #6b5537;
	--color-link-hover: #fff;
	--color-content-title-sub: #6b5537;
    color: var(--color-text);
    background-color: var(--color-bg);
    --cursor-stroke: #6b5537;
    --cursor-fill: none;
    --cursor-stroke-width: 1px;
	font-family: bilo, -apple-system, BlinkMacSystemFont, Segoe UI, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
.home .tm-header {
  display:none;
}
/* Page Loader */
.js .loading::before,
.js .loading::after {
	content: '';
	position: fixed;
	z-index: 1000;
}

.js .loading::before {
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: var(--color-bg);
}

.js .loading::after {
	top: 50%;
	left: 50%;
	width: 60px;
	height: 60px;
	margin: -30px 0 0 -30px;
	border-radius: 50%;
	opacity: 0.4;
	background: var(--color-link);
	animation: loaderAnim 0.7s linear infinite alternate forwards;

}
.heading
  h1{
    font-weight: bold;
    text-transform: uppercase;
  }
.container{
    /* display: flex;
    flex-direction: column;
    width: 100vw;
    position: relative;
    align-items: center;
    justify-content: center; */
	  height: calc(100vh);
    background-color: black;
}
@media (any-pointer: fine) {
	.cursor {
		position: fixed;
		top: 0;
		left: 0;
		display: block;
		pointer-events: none;
	}
	.cursor__inner {
		fill: var(--cursor-fill);
		stroke: var(--cursor-stroke);
		stroke-width: var(--cursor-stroke-width);
	}
}
</style>