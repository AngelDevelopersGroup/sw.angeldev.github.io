<template>
	<article class="main">
		<div class="block-text block-text-first">
			<h1 class="name"><span class="first-word">Исключительная</span> независимость</h1>
			<p class="desc">Предложенный нами русификатор можно использовать в любое время, при любой погоде, с любой версией игры. Больше никакое обновление, никакой внезапный патч не сможет насмехаться над вашим языковым барьером! Обнови игру, переустанови патч и продолжай крабить!</p>
		</div>
		<div class="block-text block-text-second">
			<h1 class="name"><span class="first-word">Простая</span> установка</h1>
			<p class="desc">
				Чтобы русифицировать игру, достаточно сделать несколько элементарных действий:<br/>
				<ol>
					<li><a href="#">Скачать</a> патчер</li>
					<li>Запустить патчер</li>
					<li>Выбрать папку с игрой</li>
					<li><a href="#">Заглянуть к нами в дискорд</a> и сказать, что вы нас любите</li>
					<li>Пока вы это делали, игра уже русифицировалась</li>
					<li>Готово! Вы восхитительны!</li>
				</ol>
			</p>
		</div>

		<div ref="img_logo" class="img-def img-logo"></div>
		<div ref="img_stella" class="img-def img-stellaonelove"></div>

		<audio ref="bg_music">
			<source src="../../assets/sound/GrassCover.mp3" />
		</audio>
	</article>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class loadings extends Vue {
	public mounted() {
		// @ts-ignore
		this.$nextTick().then(() => {
			const anim_logo = 'img-logo-anim 1.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0s 1 normal forwards';

			// @ts-ignore
			const img_logo = this.$refs.img_logo as HTMLElement;

			img_logo.style.animation = anim_logo;


			const stella_anim_hide_func = () => {
				const anim_stella = 'img-stellaonelove-hide-anim 1.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0s 1 normal forwards';

				// @ts-ignore
				const img_stellaonelove = this.$refs.img_stella as HTMLElement;

				const stella_anim_bg_music_play_func = (e: Event) => {
					// @ts-ignore
					e.target.removeEventListener(e.type, stella_anim_bg_music_play_func);
					background_music_play();
				};

        img_stellaonelove.addEventListener('webkitAnimationEnd', (e: Event) => {
          stella_anim_bg_music_play_func(e);        
        }, false);

        img_stellaonelove.addEventListener('animationend', (e: Event) => {
          stella_anim_bg_music_play_func(e);        
        }, false);

				img_stellaonelove.style.animation = anim_stella;
			};

			const stella_anim_show_func = () => {
				const anim_stella = 'img-stellaonelove-anim 300s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0s 1 normal forwards';

				// @ts-ignore
				const img_stellaonelove = this.$refs.img_stella as HTMLElement;

				img_stellaonelove.style.animation = anim_stella;
			};

			// @ts-ignore
			const bg_music = this.$refs.bg_music as HTMLAudioElement;
			bg_music.onended = (e: Event) => {
				stella_anim_hide_func();
			};

			const fucking_chrome_crutch_play = (audio: HTMLAudioElement) => {
				audio.play().then(() => {
					stella_anim_show_func();
				}).catch(() => {
					setTimeout(fucking_chrome_crutch_play, 1000, audio);
				});
			};


			const background_music_play = () => {
				// @ts-ignore
				const audio = this.$refs.bg_music as HTMLAudioElement;
				audio.pause();
				audio.currentTime = 0;

				fucking_chrome_crutch_play(audio);
			};

			const logo_anim_func = (e: Event) => {
				// @ts-ignore
				e.target.removeEventListener(e.type, logo_anim_func);
				background_music_play();
			};

      img_logo.addEventListener('webkitAnimationEnd', (e: Event) => {
        logo_anim_func(e);        
      }, false);

      img_logo.addEventListener('animationend', (e: Event) => {
        logo_anim_func(e);        
      }, false);
		});
  };
};
</script>

<style>
.block-text {
	width: 50vw;
	position: absolute;
	max-width: 450px;

	opacity: 0;
	filter: blur(5px);

	animation: block-text-anim 1.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0s 1 normal forwards;
}

.block-text-first {
	top: 10vh;
	left: 1vw;
}
.block-text-second {
	bottom: 10vh;
	right: 1vw;
}

.name {
	margin-top: 0;
	font-weight: 300;
	text-transform: uppercase;
}
.first-word {
	font-weight: 700;
}

.desc {
	font: 300 12pt 'Noto Sans', sans-serif;
}

.block-text:nth-child(1) {
	animation-delay: 1.8s !important;
}

.block-text:nth-child(2) {
	animation-delay: 3.6s !important;
}

@keyframes block-text-anim {
	50% {
		filter: blur(1px);
	}
	to {
		filter: blur(0px);
		opacity: 1;
		transform: translateZ(0);
	}
}

.img-def {
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	top: 0;
	background-size: contain !important;
	z-index: -1;
}
.img-logo {
	background: url("../../assets/fansite_logo.png") no-repeat center center;
}

@keyframes img-logo-anim {
	from {
		opacity: 0;
		transform: scale(2.2);
		filter: blur(5px);
	}
	50% {
		filter: blur(1px);
	}
	80% {
		filter: blur(0px);
		opacity: 1;
		transform: scale(0.9);
	}
	to {
		filter: blur(10px);
		opacity: 0;
		transform: scale(0.6);
	}
}

.img-stellaonelove {
	top: -10vh;
	bottom: -10vh;
	background: url("../../assets/stella_onelove.png") no-repeat center center;
	opacity: 0;
}

@keyframes img-stellaonelove-anim {
	from {
		filter: blur(10px);
		opacity: 0;
		transform: scale(2.2);
	}
	1% {
		filter: blur(1px);
		opacity: 0.75;
		transform: scale(1.3);
	}
	to {
		filter: blur(1px);
		opacity: 0.90;
		transform: scale(0.8);
	}
}

@keyframes img-stellaonelove-hide-anim {
	from {
		filter: blur(1px);
		opacity: 0.90;
		transform: scale(0.8);
	}
	50% {
		filter: blur(10px);
	}
}
</style>
