<template lang="pug">
	section.countries
		.container
			ul.countries__filter.filter
				li.filter__item(v-for="filterItem in COUNTRIES_FILTER" :key="filterItem.id" :class="[ filterItem.type, {active: filterItem.isActive} ]" @click="selectFilterItem") 
					| {{filterItem.title}}

			.countries__wrap
				.countries__row
					.countries__col.countries__col--big
						.countries__row
							.countries__card-wrap.countries__col.countries__col--25(v-for="country in COUNTRIES.slice(0, 4)" :key="country.id")
								CountriesCard(:countries_data="country")
					.countries__card-wrap.countries__col.countries__col--big.order(v-for="country in COUNTRIES.slice(4, 5)" :key="country.id")
						CountriesCardBig(:countries_data="country")

					.countries__card-wrap.countries__col.countries__col--25(v-for="country in COUNTRIES.slice(5)" :key="country.id")
						CountriesCard(:countries_data="country")
</template>

<script>
import CountriesCard from '@/components/layout/CountriesCard';
import CountriesCardBig from '@/components/layout/CountriesCardBig';
import { mapGetters } from 'vuex'

export default {
	name: 'Index',
	components: {
		CountriesCard,
		CountriesCardBig 
	},
	computed: {
		...mapGetters([
			"COUNTRIES",
			"COUNTRIES_FILTER"
		])
	},
	methods: {
		selectFilterItem: function(event) {
			let countriesMenu = document.querySelector('.countries__filter'),
        linkItem = countriesMenu.querySelectorAll('li'),
        countriesBlock = document.querySelectorAll('.card');

			let target = Array.from(event.target.classList).filter(cls=>cls!=='filter__item')[0];
        
        for (let i = 0; i < linkItem.length; i++) {


            if (linkItem[i].classList.contains(target)) {
                linkItem[i].classList.add('active');

                for (let j = 0; j < countriesBlock.length; j++) {

                    if (countriesBlock[j].classList.contains(target)) {
                        countriesBlock[j].classList.remove('disabled');
                        countriesBlock[j].classList.add('no-disabled');

                    
                    } else {
                        countriesBlock[j].classList.remove('no-disabled');
                        countriesBlock[j].classList.add('disabled');
                    }
                }

            } else {
                if (target.match(/\bactive\b/)) {
                    break;
                } else {
                    linkItem[i].classList.remove('active');
                }

            }
        }
		}
	}
}
</script>


<style lang="stylus">
	.countries
		padding 61px 0
		&__row
			display flex
			flex-wrap wrap
			margin 0 -10px
			height 100%
		&__col
			position relative
			flex 0 0 25%
			max-width 25%
			width 100%
			padding 0 10px
			@media(max-width: 991px)
				flex 0 0 50%
				max-width 50%
			@media(max-width: 575px)
				flex 0 0 100%
				max-width 100%
		&__col--big
			position relative;
			flex 0 0 50%;
			max-width 50%;
			width 100%;
			padding 0 10px;
			@media(max-width: 991px)
				flex 0 0 100%
				max-width 100%
			&.order 
				@media(max-width: 991px)
					order -1
			.countries__col
				position relative;
				flex 0 0 50%;
				max-width 50%;
				width 100%;
				padding 0 10px;
				@media(max-width: 575px)
					flex 0 0 100%
					max-width 100%
		&__col--25
			flex 0 0 25%
			max-width 25%
			@media(max-width: 991px)
				flex 0 0 50%
				max-width 50%
			@media(max-width: 575px)
				flex 0 0 100%
				max-width 100%

	.filter
		ff $pt
		display flex
		align-items center
		margin 0 0 21px
		padding 0
		list-style none
		color #9fa2a8
		font-size 12px
		font-weight 400
		font-style normal
		letter-spacing 0.6px
		line-height 16px
		text-transform uppercase
		white-space nowrap

		@media(max-width 575px) 
			overflow auto

		&__item
			position relative
			padding-bottom 2px
			cursor pointer
			transition color 0.25s
			&:not(:last-child) 
				margin-right 25px
			
			&:after 
				content ''
				position absolute
				left 0
				bottom 0
				width 100%
				height 2px
				background-color transparent
			
			&:hover 
				color #242526
			

			&.active 
				color #242526
				font-weight 700
				&:after 
					background-color #242526
                
</style>