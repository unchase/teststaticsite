<template>
	<form novalidate class="md-layout" @submit.prevent="validateUser" @reset.prevent="clearForm">
		<md-card class="md-layout-item md-size-50 md-small-size-100">
			<md-card-header>
				<div class="md-title">Новый пользователь</div>
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
<template>