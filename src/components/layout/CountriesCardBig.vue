<template lang="pug">
	article.countries__card.card.card--big.all(:class="`${ countries_data.type }`")
		.card__image-wrapper
			img.card__image(:src="require(`../../assets/img/${countries_data.images.image1}`)")
		router-link.card__title(to="") {{ countries_data.title }}
		ol.card__list-countries
			li.card__country
				router-link.card__link(to="")
					| {{ countries_data.countriesList.country1 }}
			li.card__country
				router-link.card__link(to="")
					| {{ countries_data.countriesList.country2 }}
			li.card__country
				router-link.card__link(to="")
					| {{ countries_data.countriesList.country3 }}
			li.card__country
				router-link.card__link(to="")
					| {{ countries_data.countriesList.country4 }}
			li.card__country
				router-link.card__link(to="")
					| {{ countries_data.countriesList.country5 }}

</template>

<script>

export default {
	
	name: 'CountriesCardBig',
	props: {
		countries_data: {
			type: Object,
			default() {
				return {}
			}
		}
	},
	components: {
		
	},
	data() {
		return {

		}
	},
}
</script>

<style lang="stylus">
	.countries
		&__card-wrap
			margin-bottom 20px

	.card
		card(#e6e6e6)
		&--big
			padding 87px 30px 52px
			.card__image-wrapper
					position absolute
					top 0
					left 0
					right 0
					bottom 0
					width 100%
					height 100%
			.card__image
					width 100%
					height 100%
					object-fit cover
			.card__title
					ff $nb
					position relative
					display block
					margin-bottom 43px
					font-size 40px
					font-weight 400
					line-height 29px
					color #fff
					text-decoration none
					transition 0.25s
					@media(max-width:575px)
						font-size 36px
					&:hover
						color darken(white, 15%)
			.card__list-countries
					position relative
					margin 0
					padding-left 34px
					ff $nb
					list-style-type decimal
			.card__country
					color #fff
					font-size 20px
					font-weight 400
					line-height 24px
					&:not(:last-child)
						margin-bottom 22px
			.card__link
					color inherit
					text-decoration none
					transition 0.25s
					&:hover
						color darken(white, 15%)
</style>