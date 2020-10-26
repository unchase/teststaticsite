<template>
    <!--<nav class="green lighten-1">
        <div class="nav-wrapper container">
            <div class="col s12">
                <router-link to="/" class="brand-logo">Awesome Russian IT</router-link>
                <ul id="nav-mobile" class="right hide-on-med-and-down">
                    <li><router-link to="/">Домашняя</router-link></li>
                    <li><router-link to="/events">События</router-link></li>
                    <li><router-link to="/podcasts">Подкасты</router-link></li>
                    <li><router-link to="/blogs">Блоги</router-link></li>
                    <li><router-link to="/channels">Каналы</router-link></li>
                </ul>
            </div>
        </div>
    </nav>-->
    <!--<div>
        <md-tabs md-sync-route class="md-accent" md-alignment="left">
            <md-tab id="tab-home" md-icon="home" md-label="Домашняя" to="/" exact><router-view></router-view></md-tab>
            <md-tab id="tab-events" md-label="События" md-icon="pages" to="/events"><router-view></router-view></md-tab>
            <md-tab id="tab-events" md-label="Подкасты" md-icon="pages" to="/podcasts"><router-view></router-view></md-tab>
            <md-tab id="tab-events" md-label="Каналы" md-icon="pages" to="/channels"><router-view></router-view></md-tab>
            <md-tab id="tab-blogs" md-label="Блоги" md-icon="pages" to="/blogs"><router-view></router-view></md-tab>
        </md-tabs>
    </div>-->

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
                <v-tab href="./events">События</v-tab>
                <v-tab href="./podcasts">Подкасты</v-tab>
                <v-tab href="./youtube-channels">YouTube-каналы</v-tab>
                <v-tab href="./telegram-cjannels">Telegram-каналы</v-tab>
                <v-tab href="./blogs">Блоги</v-tab>
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