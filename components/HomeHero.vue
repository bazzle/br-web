<template>
<section name="intro" id="intro" class="panel panel--white-darken panel-intro">
	<div class="panel__inner">
			<div class="cp intro">
				<div class="intro__inner">
					<h1 class="intro__title">
						{{ heroData.fields.introTitle }}
					</h1>
					<div class="intro__statement">
						<p>
							{{ heroData.fields.introStatement }}
						</p>
					</div>
					<div class="intro__links">
						<a v-for="link in links" :href="link.href" target="_blank" :key="link.id">
							{{link.linkText}}
						</a>
					</div>

					<div class="intro__down-icon">
							<svg role="img" class="intro__down-icon__icon">
								<use xlink:href="assets/svg/icons.svg#icon-arrow"></use>
							</svg>
					</div>

				</div>
		</div>
	</div>
</section>
</template>
<script>
  export default {
		name: 'HomeHero',
		props: ['heroData', 'links']
	}
</script>





<style lang="scss" scoped>

	.intro{
		@include align-left;
		position:relative;
		padding-top:$text-padding-std*2;
		padding-bottom:$text-padding-std*2;
		@include bp($bp1){
			padding-top:$text-padding-std*4;
			padding-bottom:$text-padding-std*4;
			box-sizing:content-box;
			height: calc(100vh - 80px);
			max-height:600px;
		}
		&__title{
			display:block;
			text-align:center;
			@include text-leadin-large;
			font-weight:$bold;
			margin-bottom:$text-padding-std;
			@include bp($bp2){
				font-weight:$bold;
			}
		}
		&__inner{
			width:100%;
			margin:0 auto;
			@include bp($bp2){
				width:70%;
			}
		}
		&__statement{
			padding-bottom:$text-padding-std;
			p{
				@include text-leadin-hero;
				text-align:center;
				margin-bottom:$text-padding-std;
				&:last-of-type{
					margin-bottom:0;
				}
			}
		}
		&__down-icon {
			@include align-center;
			&__icon{
				color:$color-feint;
				width: 30px;
				height: 30px;
			}
		}
		&__links{
			width:100%;
			padding-bottom:$text-padding-std;
			text-align:center;
			display:flex;
			justify-content: center;
			align-items:center;
			flex-direction:row;
			font-size:2.3rem;
			font-weight:$std;
			a{
				@include text-underline($color-brand);
				padding:.2em;
			}
			@include bp($bp2){
				font-size:2.3rem;
			}
		}
		&__statement-cta{
			@include text-underline($color-brand);
		}
	}

</style>
