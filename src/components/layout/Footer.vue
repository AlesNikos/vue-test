<template lang="pug">
	footer.footer
		.container 
			.footer__inner
				p.footer__copy © 2013 - 2015
				a.footer__dev(href="#")
					p.footer__dev-text Одна ошибка и 
						span ты ошибся
					<FooterLogo />
</template>

<script>
import FooterLogo from '@/assets/img/footer_logo.svg';

export default {
	name: 'Footer',
	components: {
		FooterLogo,
	}
}

</script>