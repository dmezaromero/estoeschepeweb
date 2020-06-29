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
<style>
.grid {
	pointer-events: none;
	position: absolute;
	width: 100%;
	height: 100%;
	top: -5%;
	left: -5%;
	display: grid;
	grid-template-columns: repeat(50,2%);
	grid-template-rows: repeat(50,2%);
}

.grid__item {
	position: relative;
}

.grid--img .grid__item {
	overflow: hidden;
	display: flex;
	align-items: center;
	justify-content: center;
	will-change: transform;
}

.grid__item-img {
	position: relative;
	width: 100%;
	height: 100%;
	background-size: cover;
	background-position: 50% 50%;
}

.grid--img .grid__item-img {
	flex: none;
	width: calc(100% + 100px);
	height: calc(100% + 100px);
	will-change: transform;
}
/* Shorthand grid-area: grid-row-start / grid-column-start / grid-row-end / grid-column-end */

.pos-0 {
	grid-area: 9 / 3 / 23 / 9;
}

.pos-1 {
	grid-area: 1 / 18 / 12 / 28;
}

.pos-2 {
	grid-area: 1 / 36 / 14 / 42;
}

.pos-3 {
	grid-area: 13 / 11 / 32 / 18;
}

.pos-4 {
	grid-area: 17 / 38 / 33 / 45;
}

.pos-5 {
	grid-area: 20 / 46 / 28 / 51;
}

.pos-6 {
	grid-area: 35 / 1 / 51 / 10;
}

.pos-7 {
	grid-area: 36 / 13 / 47 / 23;
}

.pos-8 {
	grid-area: 40 / 26 / 51 / 32;
}

.pos-9 {
 	grid-area: 37 / 39 / 48 / 47;
}
</style>