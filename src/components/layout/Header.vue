<template lang="pug">
	header.header
		.container
			.header__inner
				a.header__logo(href="#")
					<HeaderLogo />
				.header__title-wrap
					.header__title adventure
					.header__subtitle сделай красиво, чтобы было красиво
</template>

<script>
import HeaderLogo from '@/assets/img/logo.svg';

export default {
	name: 'Header',
	components: {
		HeaderLogo,
	}
}

</script>
