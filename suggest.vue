<template>
	<form novalidate class="md-layout md-alignment-center" @submit.prevent="validateUser" @reset.prevent="clearForm">
		<md-card class="md-layout-item md-size-50 md-small-size-100">
			<md-card-header>
				<div class="md-title">Предложить {{ title }}</div>
			</md-card-header>
			<md-card-content>
				<p>
					Вы можете предложить новый {{ title.toLowerCase() }}, заполнив следующую форму 
					с указанными ниже полями, каждое из которых является необязательным, если не указано иное. 
					Или <a :href="url">создав pull request в проекте awesome-russian-it вручную</a>,
					содержащий новый файл с расширением <code>.yml</code>, который содержит необходимые поля.
				</p>
				<md-divider></md-divider>
				<div class="md-layout md-gutter md-alignment-center">
					<div class="md-layout-item md-small-size-100">
						<md-field v-for="(field, idx) in fields" :key="field.name">
							<label for="field.name">{{ field.label }}</label>
							<md-input :id="field.name" :name="field.name" type="text" v-model="form.values[idx]" :required="field.required"></md-input>
							<span class="md-helper-text">{{ field.description }}</span>
						</md-field>
					</div>
				</div>
			</md-card-content>
			<md-card-actions>
				<md-button class="md-raised" type="reset">СБРОСИТЬ</md-button>
				<md-button class="md-primary" type="submit">СОЗДАТЬ</md-button>
			</md-card-actions>
		</md-card>
		
		<md-snackbar md-position="center" :md-duration="duration" :md-active.sync="showClearSnackbar" md-persistent>
			<span>Значения полей были сброшены.</span>
			<md-button class="md-primary" @click="showClearSnackbar = false">ОК</md-button>
		</md-snackbar>
	</form>
</template>

<script>
	module.exports = {
		name: 'suggest',
		mixins: [validationMixin],
		props: [
			'title',
			'fields',
			'url'
		],
		data: function() {
			return {
				duration: 2000,
				showClearSnackbar: false,
				form: {
					values: []
				}
			}
		},
		//validations: {
		//	form: {
		//		firstName: {
		//		  required,
		//		  minLength: minLength(3)
		//		},
		//		lastName: {
		//		  required,
		//		  minLength: minLength(3)
		//		}
		//	}
		//},
		methods: {
			mounted: function(){
				console.log('mounted()');
				alert('mounted()');
			},
			createPullRequest() {
				var self = this;
				var content = "";
				if (this.fields.length > 0)
				{
					this.fields.forEach(function(field, index) {
						if(self.form && self.form.values[index]) {
							var value = self.form.values[index].trim();
							if(value && value.length > 0) {
								if(field.multiple) {
									content = content + field.name + ":\n";
									value.split(",").forEach(function(part) {
										content = content + "  - " + part.trim() + "\n";
									});
								} else {
									content = content + field.name + ": " + value + "\n";
								}
							}
						}
					});
				}
				if(content.length > 0) {
					content = encodeURIComponent(content);
					window.location.href = self.url + "?value=" + content;
				}
				
				// Instead of this timeout, here you can call your API
				window.setTimeout(() => {
				  this.clearForm()
				}, 1500)
			},
			getValidationClass (fieldName) {
				const field = this.$v.form[fieldName]

				if (field) {
					return {
						'md-invalid': field.$invalid && field.$dirty
					}
				}
			},
			clearForm () {
				//this.$v.$reset();
				if (this.fields.length > 0)
				{
					this.fields.forEach(function(field, index) {
						if(self.form && self.form.values[index]) {
							var value = self.form.values[index].trim();
							if(value && value.length > 0) {
								if(field.multiple) {
									value = [];
								} else {
									value = null;
								}
							}
						}
					});
					showClearSnackbar = true;
				}
			},
			validateUser () {
				//this.$v.$touch()

				//if (!this.$v.$invalid) {
				  this.createPullRequest()
				//}
			}
		}
	}
</script>