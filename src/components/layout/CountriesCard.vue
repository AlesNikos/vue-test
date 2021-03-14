<template lang="pug">
	article.countries__card.card.all(:class="`${ countries_data.type }`")
		swiper.swiper(ref="mySwiper" :options="swiperOptions")
				swiper-slide.swiper-slide
						.card__slide.slide.slide--1
								.slide__image-wrapper
									img.slide__image(:src="require(`../../assets/img/${countries_data.images.image1}`)")
								router-link.slide__title(to="") {{ countries_data.title }}
				swiper-slide.swiper-slide
						.card__slide.slide.slide--2
								.slide__text {{ countries_data.text }}
								router-link.slide__title(to="") {{ countries_data.title }}
				swiper-slide.swiper-slide
						.card__slide.slide.slide--3
								.slide__image-wrapper
									img.slide__image(:src="require(`../../assets/img/${countries_data.images.image2}`)")
								.slide__btn-wrap.btn-wrap
										button.slide__btn.js-btn-show(:data-src="require(`../../assets/img/${countries_data.images.imageBig}`)" @click="openLightboxOnSlide(1)")
											IconZoom
								router-link.slide__title(to="") {{ countries_data.title }}
				swiper-slide.swiper-slide
						.card__slide.slide.slide--4
								.slide__image-wrapper
									img.slide__image(:src="require(`../../assets/img/${countries_data.images.image3}`)")
								.slide__btn-wrap.btn-wrap
										button.slide__btn.js-btn-play(:data-src="`${countries_data.video}`" @click="openLightboxOnSlide(2)")
											IconPlay
								router-link.slide__title(to="") {{ countries_data.title }}
				.swiper-button-prev(slot="button-prev")
					ArrowLeft
				.swiper-button-next(slot="button-next")
					ArrowRight
		FsLightbox(:toggler="toggler" :slide="slide" :sources="[require(`../../assets/img/${bigImageLink}`), videoLink]")

</template>

<script>
import FsLightbox from "fslightbox-vue";
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
import ArrowLeft from '@/assets/img/icons/prev_slide.svg';
import ArrowRight from '@/assets/img/icons/next_slide.svg';
import IconZoom from '@/assets/img/icons/icon_zoom.svg';
import IconPlay from '@/assets/img/icons/icon_play.svg';

export default {
	
	name: 'CountriesCard',
	props: {
		countries_data: {
			type: Object,
			default() {
				return {}
			}
		}
	},
	components: {
		FsLightbox,
		Swiper,
		SwiperSlide,
		ArrowLeft,
		ArrowRight,
		IconZoom,
		IconPlay
	},
	data() {
		return {

			toggler: false,
			slide: 1,
			swiperOptions: {
				speed: 500,
				// loop: true,
				slidesPerView: 1,
				effect: 'fade',
				navigation: {
					nextEl: '.swiper-button-next',
					prevEl: '.swiper-button-prev'
				}
			},
			bigImageLink: '',
			videoLink: ''
		}
	},
	created () {
				this.bigImageLink = this.countries_data.images.imageBig;
				this.videoLink = this.countries_data.video;

	},
	methods: {
		openLightboxOnSlide: function(number) {
			this.slide = number;
			this.toggler = !this.toggler;
		}
	}
}
</script>

<style lang="stylus">
	.countries
		&__card-wrap
			margin-bottom 20px

	.card
		card(#e6e6e6)
		&.disabled
			opacity 0.2
			pointer-events none
			.swiper-slide
				display flex
				align-items center
				justify-content center
				pointer-events none
			.slide
				width 240px
				height 160px
				@media(max-width: 575px)
					width 100%
					height 100%
			.swiper-button-next,
			.swiper-button-prev
				display none
	.slide
		position relative
		width 100%
		height 100%
		&__title
			position absolute
			text-decoration none
			transition 0.25s
			color #fff
			font-weight 400
			ff $nb
			z-index: 1
		&__image 
			width 100%
			height 100%
			object-fit cover
		&--1
			background-color: rgba(3, 21, 36, 0.6)
			.slide__image-wrapper
				position: absolute
				top 0
				right 0
				bottom 0
				left 0
				width 100%
				height 100%
			.slide__title
				top 52%
				left 50%
				transform translate(-50%, -50%)
				font-size 36px
				font-style normal
				letter-spacing normal
				line-height 36px
				white-space nowrap
				&:hover
					color darken(white, 15%)
		&--2
			padding 35px 38px 41px 20px
			background-color #313336
			.slide__title
				bottom 17px
				left 20px
				font-size 24px
				line-height 24px
				&:hover
					color darken(white, 15%)
			.slide__text
				ff $pt
				max-height 88px
				color #abaeb3
				font-size 14px
				font-weight 400
				line-height 22px
				letter-spacing 0.01em
				overflow hidden
		&--3
			background-color rgba(7, 26, 42, 0.2)
			.slide__image-wrapper
				position absolute
				top 0
				right 0
				bottom 0
				left 0
				width 100%
				height 100%
			.slide__title
				bottom 17px
				left 20px
				font-size 24px
				line-height 24px
				&:hover
					color darken(white, 15%)
			.slide__btn
				position absolute
				left 50%
				top 50%
				transform translate(-50%, -50%)
				width 42px
				height 42px
				border 0
				padding 0
				cursor pointer
				z-index 2
				outline none
		&--4
			background-color: rgba(7, 26, 42, 0.2)
			.slide__image-wrapper
				position absolute
				top 0
				right 0
				bottom 0
				left 0
				width 100%
				height 100%
			.slide__title
				bottom 17px
				left 20px
				font-size 24px
				line-height 24px
				&:hover
					color darken(white, 15%)
			.slide__btn
				position absolute
				left 50%
				top 50%
				transform translate(-50%, -50%)
				width 42px
				height 42px
				border 0
				padding 0
				cursor pointer
				z-index 2
				outline none
	.swiper-slide
		height auto
	.swiper-container
		width 100%
		height 100%
	.swiper-button-next,
	.swiper-button-prev
		top inherit
		bottom 10%
		width 22px
		height 22px
		opacity 0.15
		border-radius 50%
		transition 0.25s
		&:hover
			opacity 0.5
	.swiper-button-next
		right: 20px
		&:after
			display none
	.swiper-button-prev
		left inherit
		right 57px
		&:after
			display none
	.swiper-button-prev.swiper-button-disabled, 
	.swiper-button-next.swiper-button-disabled
		opacity 0.15

	.fslightbox-slide-number-container
		display none
	.fslightbox-toolbar-button
		&:first-child
			display none
	.fslightbox-toolbar
		bgc(transparent)
</style>