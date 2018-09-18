<template>
	<div id='particles-js'></div>
</template>

<script>
import 'particles.js';

export default {
	name: 'ParticlesJS',

	mounted() {
		this.$nextTick(() => {
			particlesJS('particles-js', {
				particles: {
					number: {
						value: 80,
						density: {
							enable: true,
							value_area: 800,
						},
					},
					color: {
						value: '#f7b8fe',
					},
					shape: {
						type: 'circle',
						stroke: {
							width: 0,
							color: '#000000',
						},
						polygon: {
							nb_sides: 5,
						},
						image: {
							src: 'img/github.svg',
							width: 100,
							height: 100,
						},
					},
					opacity: {
						value: 0.5,
						random: false,
						anim: {
							enable: false,
							speed: 1,
							opacity_min: 0.1,
							sync: false,
						},
					},
					size: {
						value: 3,
						random: true,
						anim: {
							enable: false,
							speed: 40,
							size_min: 0.1,
							sync: false,
						},
					},
					line_linked: {
						enable: true,
						distance: 150,
						color: '#f453fd',
						opacity: 0.4,
						width: 1,
					},
						move: {
						enable: true,
						speed: 2,
						direction: 'none',
						random: false,
						straight: false,
						out_mode: 'out',
						bounce: false,
						attract: {
							enable: false,
							rotateX: 600,
							rotateY: 1200,
						},
					},
				},
				interactivity: {
					detect_on: 'canvas',
					events: {
							onhover: {
									enable: false,
									mode: 'repulse',
							},
							onclick: {
									enable: false,
									mode: 'push',
							},
							resize: true,
					},
					modes: {
						grab: {
							distance: 800,
							line_linked: {
								opacity: 1,
							},
						},
						bubble: {
							distance: 400,
							size: 40,
							duration: 2,
							opacity: 8,
							speed: 3,
						},
						repulse: {
							distance: 200,
							duration: 0.4,
						},
						push: {
							particles_nb: 4,
						},
						remove: {
							particles_nb: 2,
						},
					},
				},
				retina_detect: true,
			});
		});
	},
};
</script>

<style>
#particles-js {
	z-index: -3;
	position: absolute;
	width: 100%;
	height: 100%;
	background-color: #141414;
	background-image: url("");
	background-repeat: no-repeat;
	background-size: cover;
	background-position: 50% 50%;

	animation: particles-js-anim 5s cubic-bezier(0.25, 0.46, 0.45, 0.94) 1.8s 1 normal forwards;
	opacity: 0;
}

@keyframes particles-js-anim {
	60% {
		opacity: 1;
	}
	to {
		filter: blur(2px);
		opacity: 1;
	}
}
</style>