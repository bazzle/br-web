<template>
  <section id="about" class="panel panel--white-darken panel-about">
	<div class="cp about">
    <div class="panel__inner about__inner">
      <div class="row">
				<div class="about__maintext">
						<p>
							{{ this.title }}
						</p>
				</div>
				<div class="about__profile">
						<div class="about__profile__content">
							<div class="about__links">
								<a v-for="link in links" :href="link.href" target="_blank" :key="link.id">
									{{link.linkText}}
								</a>
							</div>
						</div>
				</div>
      </div>
    </div>
	</div>
</section>
</template>
<script>
  export default {
		name: 'aboutMe',
		data(){
			return{
				title: 'Feel free to get in touch'
			}
		},
		props: ['links']
  }
</script>





<style lang="scss" scoped>
.about{
	&__title{
		font-weight:$bold;
		margin-bottom:$text-padding-std;
		border-bottom:2px solid $color-brand;
		display: inline-block;
		font-size:$font-size-small;
	}
	&__maintext{
		@include bp($bp2){
			padding-left:$grid-space;
			padding-right:$grid-space*2;
			width:60%;
		}
		p{
			font-weight: $std;
			font-size: 3rem;
			padding-bottom:$text-padding-std;
			font-weight: $chunky;
			line-height: 1.2;
			@include bp($bp2) {
				line-height: 1;
				font-size: 6rem;
				max-width: 800px;
			}
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
	}
</style>
