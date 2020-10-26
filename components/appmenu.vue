<template>
    <v-toolbar color="orange darken-2"
               dark
               flat
               max-height="120">
        <!--<v-icon
        large
        color="green darken-2"
    >
        mdi-domain
    </v-icon>-->

        <v-icon left>
            mdi-pencil
        </v-icon>

        <v-toolbar-title class="headline">{{ title }}</v-toolbar-title>

        <v-text-field append-icon="mdi-magnify"
                      class="mx-4"
                      flat
                      hide-details
                      label="Найти"
                      solo-inverted>
        </v-text-field>

        <template v-slot:extension>
            <v-tabs centered>
                <v-tab href="/">Домашняя</v-tab>
                <v-tab href="/events">События</v-tab>
                <v-tab href="/podcasts">Подкасты</v-tab>
                <v-tab href="/youtube-channels">YouTube-каналы</v-tab>
                <v-tab href="/telegram-cjannels">Telegram-каналы</v-tab>
                <v-tab href="/blogs">Блоги</v-tab>
            </v-tabs>
        </template>
    </v-toolbar>
</template>

<script>
    module.exports = {
        props: {
            title: {
                type: String,
                required: false,
                default: 'Awesome Russian IT'
            }
        }
    }
</script>