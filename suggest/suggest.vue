<template>
    <b-container>
        <h1 class="font-weight-bold display-4">Предложить {{ title }}</h1>
        <b-card>
            <p>
                Предложить новый {{ title.toLowerCase() }}, заполнив следующую форму или
                <a :href="url">создав pull request в проекте awesome-russian-it вручную</a>,
                содержащий новый файл с расширением <code>.yml</code>, который содержит следующие свойства,
                каждое из которых является необязательным, если не указано иное.
            </p>
            <slot></slot>
            <b-form @submit="submit">
                <b-form-group v-for="(field, idx) in fields"
                              :key="field.name"
                              :label="field.name"
                              :label-for="field.name"
                              :description="field.description">
                    <b-form-checkbox v-if="field.bool" :id="field.name" v-model="values[idx]" value="true"></b-form-checkbox>
                    <b-form-input v-else :id="field.name" type="text" v-model="values[idx]" :required="field.required"></b-form-input>
                </b-form-group>
                <b-button type="submit" variant="primary">Создать Pull Request</b-button>
            </b-form>
        </b-card>
    </b-container>
</template>

<script>
    module.exports = {
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
        methods: {
            submit(evt) {
                evt.preventDefault();
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
            }
        }
    }
</script>