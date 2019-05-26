<template>
	<div>
		<h1>{{ msg }}</h1>

		<div class="container">
			<div class="row justify-content-md-center">
				<div class="col-md-auto">
					<div class="card">
						<div class="heads card-body">
							<small><b>{{ kalkulasi || '0' }}</b></small>
							<h1>{{ hasil || '0' }}</h1>
						</div>
						<hr style="padding-top:0;margin-top:0;">
						<div class="card-body">
							
							<!-- row C() -->
							<div class="row" style="margin-bottom:10px;">
								<div class="col-md">
									<button type="button" @click="clear" class="btn btn-light clear">C</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit('(')" class="btn btn-light">(</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(')')" class="btn btn-light">)</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit('/')" class="btn btn-warning">/</button>
								</div>
							</div>

							<!-- row 789 -->
							<div class="row" style="margin-bottom:10px;">
								<div class="col-md">
									<button type="button" @click="addDigit(7)" class="btn btn-light">7</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(8)"  class="btn btn-light">8</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(9)" class="btn btn-light">9</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit('*')" class="btn btn-warning">x</button>
								</div>
							</div>

							<!-- row 456 -->
							<div class="row" style="margin-bottom:10px;">
								<div class="col-md">
									<button type="button" @click="addDigit(4)" class="btn btn-light">4</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(5)" class="btn btn-light">5</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(6)" class="btn btn-light">6</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit('-')" class="btn btn-warning">-</button>
								</div>
							</div>

							<!-- row 123 -->
							<div class="row" style="margin-bottom:10px;">
								<div class="col-md">
									<button type="button" @click="addDigit(1)" class="btn btn-light">1</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(2)" class="btn btn-light">2</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit(3)" class="btn btn-light">3</button>
								</div>
								<div class="col-md">
									<button type="button" @click="addDigit('+')" class="btn btn-warning">+</button>
								</div>
							</div>
							
							<!-- row 0 -->
							<div class="row" style="margin-bottom:10px;">
								<div class="col col-md-6">
									<button style="width:100%;" type="button" @click="addDigit(0)" class="btn btn-light">0</button>
								</div>
								<div class="col-md">
									<button type="button" @click="dot" class="btn btn-light">.</button>
								</div>
								<div class="col-md">
									<button title="Disabled" type="button" @click="backspace" class="btn btn-success">
										<v-icon name="long-arrow-alt-left"/>
									</button>
								</div>
							</div>
							
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'Calc',
		props: {
			msg: String
		},
		data() {
			return {
				kalkulasi: '',
				hasil: ''
			}
		},
		methods: {
			clear() {
				this.kalkulasi = '';
				this.hasil = '';
			},
			backspace(){
				this.kalkulasi = this.kalkulasi.substring(0, this.kalkulasi.length-1);
				this.calculate();
			},
			addDigit(num) {
				this.kalkulasi = this.kalkulasi+num;
				this.calculate();
			},
			dot() {
				if(this.kalkulasi.indexOf('.') === -1){
					this.addDigit('.');
				}
			},
			calculate() {
				this.hasil = eval(this.kalkulasi);
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.heads {
		width: 320px;
		text-align: end;
	}
	small {
		color: #bbb;
		font-size: 13px;
	}
	button {
		height: 50px;
		width: 50px;
		border-radius: 50px;
		font-weight: 600;
	}
	.btn-light {
		background-color: #eee;
		border: .5px solid #f7f7f7;
	}
	.clear {
		border-color: rgb(251,150,120, .5);
		background-color: rgb(251,150,120, .2);
		color: rgb(251,150,120);
	}
	.clear:hover {
		border-color: rgb(251,150,120);
		background-color: rgb(251,150,120);
		color: #fff;
	}
	.btn-warning {
		color: #fff;
	}
	.container {
		margin-top: 20px;
	}
	h3 {
		margin: 40px 0 0;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	li {
		display: inline-block;
		margin: 0 10px;
	}
	a {
		color: #42b983;
	}
	.calc {
		border: 1px solid #333;
		border-radius: 10px;
	}
</style>
