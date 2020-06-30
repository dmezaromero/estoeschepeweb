<template>
          <div class="background-images">
        <div class="grid" >
                <div :class="'grid__item pos-' + index" v-for="(image, index) in images" v-bind:key="image.id">
                    <div class="grid__item-img" :style="'background-image:url('+image.url+');'">
                    </div>
                </div>
        </div>
    </div>
</template>
<script>
if (process.client) {
	require('~/plugins/demo1/index.js')
}

export default {
    props:{
        images: Array
	}
}
</script>