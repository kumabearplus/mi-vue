<template>
	<div class="content"
		:class="content.type">
		<h3 class="title">{{content.title}}</h3>
		<div class="slide-wrap">
			<span
				@click="slidePre()"
				class="slide-pre">
				<i class="iconfont">&#xe621;</i>
			</span>
			<span
				@click="slideNext()"
				class="slide-next">
				<i class="iconfont">&#xe606;</i>
			</span>
			<ul class="sub-content clearfix"
				:style="{'margin-left': this.currPage * (-296) + 'px'}">
				<li class="content-item"
					v-for="item in content.list">
					<template v-if="item.type === 0">
						<a :href="item.sourceUrl" target="_blank">
							<h3 class="subTitle">{{item.title}}</h3>
							<p class="desc first-desc">
								{{item.desc}}
							</p>
							<img class="content-image" :src="item.imgUrl" alt="" />
						</a>
					</template>
					<template v-if="item.type === 1">
						<a :href="item.sourceUrl" target="_blank">
							<h3 class="subTitle">{{item.title}}</h3>
							<p class="desc">
								{{item.desc}}
							</p>
							<p class="price">
								{{item.price}}
							</p>
							<img class="content-image" :src="item.imgUrl" alt="" />
						</a>
					</template>
					<template v-if="item.type === 2">
						<p class="desc">
							{{item.desc1}}<br/>{{item.desc2}}
						</p>
						<a :href="item.sourceUrl" target="_blank">
							<p class="btn-txt">
								{{item.btnTxt}}
							</p>
						</a>
						<img class="content-image" :src="item.imgUrl" alt="" />
					</template>
				</li>
			</ul>
			<template v-if="content.length === 3">
				<ul class="dot-list">
					<li class="dot-item"
						v-for="n in 3"
						:class="{active: n === currPage + 1 }" :key="n">
						<span class="dot" @click="play(n-1)"></span>
					</li>
				</ul>
			</template>
			<template v-if="content.length === 4">
				<ul class="dot-list">
					<li class="dot-item"
						v-for="n in 4"
						:class="{active: n === currPage + 1 }" :key="n">
						<span class="dot" @click="play(n-1)"></span>
					</li>
				</ul>
			</template>
			
		</div>
	</div>
</template>

<script>
export default {
	data () {
		return {
			currPage: 0
		}
	},
	props: {
		content: {
			required: true,
			type: Object
		}
	},
	methods: {
		slidePre () {
			if (this.currPage !== 0) {
				this.currPage--
			}
		},
		slideNext () {
			if (this.currPage < Math.floor((this.content.list.length - 1))) {
				this.currPage++
			}
		},
		play(n){
      this.currPage = n
    }
	}
}
</script>

<style scoped lang="scss">
	.iconfont {
	  font-family:"iconfont" !important;
    font-size: 10px;
	  font-style:normal;
	  -webkit-font-smoothing: antialiased;
	  -moz-osx-font-smoothing: grayscale;
	}
.content {
	position: relative;
	float: left;
	width: 296px;
	height: auto;
	margin: 0 0 14px 14px;
	padding-top: 45px;
	background: #fff;
	transition: all 0.3s;
	&:hover {
		transform: translateY(-3px);
		box-shadow: 5px 5px 20px #ccc;
		.slide-pre, .slide-next {
			opacity: 1;
		}
	}
	&:nth-child(1) {
		margin-left: 0;
	}
	.title {
		margin: 0 10px 18px;
		font-size: 16px;
		font-weight: 400;
		text-align: center;
	}
}
.book {
	border-top: 1px solid #ffac13;
	.title {
		color: #ffac13;
	}
	.btn-txt {
		color: #ffac13;
		border: 1px solid #ffac13;
		background: #fff;
		&:hover {
			color: #fff;
			background: #ffac13;
		}
	}
	.first-desc {
		margin-bottom: 60px;
	}
}

.theme {
	border-top: 1px solid #83c44e;
	.title {
		color: #83c44e;
	}
	.btn-txt {
		color: #83c44e;
		border: 1px solid #83c44e;
		background: #fff;
		&:hover {
			color: #fff;
			background: #83c44e;
		}
	}
}

.game {
	border-top: 1px solid #e53935;
	.title {
		color: #e53935;
	}
	.btn-txt {
		color: #e53935;
		border: 1px solid #e53935;
		background: #fff;
		&:hover {
			color: #fff;
			background: #e53935;
		}
	}
}

.app {
	border-top: 1px solid #2196f3;
	.title {
		color: #2196f3;
	}
	.btn-txt {
		color: #2196f3;
		border: 1px solid #2196f3;
		background: #fff;
		&:hover {
			color: #fff;
			background: #2196f3;
		}
	}
}
.slide-wrap {
	width: 296px;
	height: 340px;
	overflow: hidden;
	.sub-content {
		width: 1200px;
		height: 340px;
		transition: all 0.5s ease;
		.content-item {
			position: relative;
			float: left;
			width: 296px;
			height: 340px;
		}
	}
	.slide-pre, .slide-next {
		display: block;
		width: 20px;
		height: 46px;
		line-height: 46px;
		font-size: 15px;
		text-align: center;
		margin-top: -24px;
		cursor: pointer;
		z-index: 11;
		background: rgba(66,66,66,0.2);
		color: #fff;
		&:hover {
			background: #b0b0b0;
		}
	}
	.slide-pre {
		position: absolute;
		left: 0;
		top: 50%;
		opacity: 0;
		transition: all 0.3s;
	}
	.slide-next {
		position: absolute;
		right: 0;
		top: 50%;
		opacity: 0;
		transition: all 0.3s;
	}
}

.subTitle {
	margin: 0 0 10px 0;
	font-weight: normal;
	font-size: 20px;
	text-align: center;
	color: #333;
}
.desc {
	margin: 0 48px 10px;
	height: 40px;
	font-size: 12px;
	line-height: 20px;
	text-align: center;
	overflow: hidden;
	color: #b0b0b0;
	width: 200px;

}
.content-image {
	display: block;
	width: 216px;
	height: 154px;
	margin: 30px auto 0;
}
.price {
  height: 21px;
  margin: 0 10px 15px;
  text-align: center;
}
.btn-txt {
	width: 118px;
  height: 28px;
  font-size: 12px;
  line-height: 28px;
	text-align: center;
	margin: 0 auto;
	margin-bottom: 14px;
	background: #fff;
	cursor: pointer;
}

.dot-list {
	display: block;
	position: absolute;
	left: 50%;
	bottom: 10px;
	width: 140px;
	text-align: center;
	margin-left: -70px;
	z-index: 11;
	.dot-item {
		display: inline-block;
    width: 10px;
    height: 10px;
    padding: 10px;
    margin: 0 2px;
    cursor: pointer;
		&.active {
			.dot {
				background: #fff;
				border: 2px solid #ff6700;
			}
		}
		.dot {
			display: block;
	    width: 6px;
	    height: 6px;
	    border: 2px solid #f5f5f5;
	    border-radius: 6px;
	    text-align: left;
	    text-indent: -9999em;
	    overflow: hidden;
	    background-color: #b0b0b0;
	    transition: all .5s;
	    &:hover {
	    	background-color: #ff6700;
	    }
		}
	}
}
</style>
