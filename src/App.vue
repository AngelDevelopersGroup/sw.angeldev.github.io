<template>
	<div id="app">
		<particlesJS/>
		<page-loading/>
	</div>
</template>

<script lang="ts">
import 'normalize.css';

import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import pageLoading from './components/pages/loading.vue';
import particlesJS from './components/ParticlesJS.vue';

@Component({
	components: {
		particlesJS,
		pageLoading,
	},
})
export default class App extends Vue {}
</script>

<style>
@import url("https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.0/normalize.min.css");
@import url('https://fonts.googleapis.com/css?family=Noto+Sans:400,700|Roboto+Condensed:700,400,300&subset=cyrillic');

html, body {
	height: 100%;
	width: 100%;
}

body {
	background-color: #141414;
	position: relative;
	overflow: hidden;
	font: 300 14pt 'Roboto Condensed', sans-serif;
	color: #fff;
}

.par {
	z-index: -2;
	width: 100vw;
	height: 150vh;
	position: absolute;
	bottom: -45vh;
	left: 0vw;
	right: 0vw;
	background: url("/img/par/new3_shadow.png") no-repeat center center;
	background-size: contain;

	display: none;
}

.par-show {
	animation-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
	animation-duration: 300s;
	animation-fill-mode: forwards;
	animation-name: parLoading;
}

.par-hide {
	animation-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
	animation-duration: 3s;
	animation-fill-mode: forwards;
	animation-name: parUnLoading;
	
}

@keyframes parLoading {
	from {
		opacity: 0;
		transform: scale(3);
	}
	5% {    
		opacity: 0.75;
		transform: scale(1.3);
	}
	to {
		opacity: 0.90;
		transform: scale(1);
	}
}

@keyframes parUnLoading {
	from {
		opacity: 0.90;
		transform: scale(1);
	}
	to {
		opacity: 0;
		transform: scale(0.3);
	}
}

.info_wrapper {
	position: absolute;
	top: 0; left: 0; bottom: 0; right: 0;

	display: flex;

	flex-direction: column-reverse;
	
	justify-content: space-between;
	align-items: baseline;
}

.link {
	padding: 1rem;
	width: 100%;
	display: flex;
	align-self: center;
	justify-content: space-evenly;
}

.link a {
	transform: translateY(5vh);

	transition: 
		opacity 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94),
		color 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);

	opacity: 0.2;
	animation-duration: 1s;
	animation-name: aLoading;
	animation-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
	animation-fill-mode: forwards;
}

.link a:nth-child(1) {
	animation-delay: 0s;
}

.link a:nth-child(2) {
	animation-delay: 0.3s;
}

.link a:nth-child(3) {
	animation-delay: 0.6s;
}

@keyframes aLoading {
	to {
		transform: translateY(0);
	}
}

a:link, a:visited {
	color: #f7b8fe;
	text-decoration: none;
}

a:hover {
	opacity: 1;
	color: #f453fd;
}
</style>
