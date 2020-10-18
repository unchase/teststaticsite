<template>
	<form novalidate class="md-layout" @submit.prevent="validateUser" @reset.prevent="clearForm">
		<md-card class="md-layout-item md-size-50 md-small-size-100">
			<md-card-header>
				<div class="md-title">предложить {{ title }}</div>
			</md-card-header>
			<md-card-content>
				<div class="md-layout md-gutter">
					<div class="md-layout-item md-small-size-100">
					<md-field :class="getValidationClass('firstName')">
						<label for="first-name">Имя</label>
						<md-input v-model="form.firstName" name="first-name" id="first-name" required />
						<span class="md-helper-text">Помощь</span>
						<span class="md-error" v-if="!$v.form.firstName.required">The first name is required</span>
						<span class="md-error" v-else-if="!$v.form.firstName.minlength">Invalid first name</span>
					</md-field>
					</div>

					<div class="md-layout-item md-small-size-100">
						<md-field :class="getValidationClass('lastName')">
							<span class="md-prefix">$</span>
							<label for="last-name">Фамилия</label>
							<md-input v-model="form.lastName" name="last-name" id="last-name" />
							<span class="md-error" v-if="!$v.form.lastName.required">Фамилия должна быть задана.</span>
							<span class="md-error" v-else-if="!$v.form.lastName.minlength">Неверная фамилия</span>
						</md-field>
					</div>
				</div>
				<div class="md-layout md-gutter">
					<div class="md-layout-item md-small-size-100">
						<md-field>
							<label for="first-name">Описание</label>
							<md-textarea v-model="form.description" name="description" id="description" />
							<md-icon>description</md-icon>
						</md-field>
					</div>
				</div>
				<div class="md-layout md-gutter">
					<div class="md-layout-item md-small-size-100">
						<md-field>
							<md-chips v-model="form.tags" name="tags" id="tags" class="md-primary" md-placeholder="Добавить тэг..." :md-auto-insert="true">
								<label>Тэги</label>
							</md-chips>
						</md-field>
					</div>
				</div>
			</md-card-content>

			<md-card-actions>
				<md-button class="md-raised" type="reset">СБРОСИТЬ</md-button>
				<md-button class="md-primary" type="submit">СОЗДАТЬ</md-button>
			</md-card-actions>
		</md-card>
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
				values: []
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
			createPullRequest() {
				var self = this;
				var content = "";
				this.fields.forEach(function(field, index) {
					if(self.values[index]) {
						var value = self.values[index].trim();
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
				this.$v.$reset();
				this.fields.forEach(function(field, index) {
					if(self.values[index]) {
						var value = self.values[index].trim();
						if(value && value.length > 0) {
							if(field.multiple) {
								value = [];
							} else {
								value = null;
							}
						}
					}
				});
			},
			validateUser () {
				this.$v.$touch()

				if (!this.$v.$invalid) {
				  this.createPullRequest()
				}
			}
		}
	}
</script>