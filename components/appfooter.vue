﻿<template>
    <div>
        <v-card class="flex"
                flat
                tile>
            <v-card-title class="orange darken-2 white--text">
                <v-btn v-for="(link, j) in links"
                       :href="link.url"
                       :key="(j + socialIcons.length + 1)"
                       dark
                       icon
                       style="margin-left: 10px;">
                    <v-icon size="30px" :v-text="link.title">{{ link.icon }}</v-icon>
                </v-btn>
                <a href="https://www.buymeacoffee.com/nikolaychebotov" style="margin-left:10px;"  target="_blank">
                    <img src="https://img.buymeacoffee.com/button-api/?text=Support me!&emoji=🙏&slug=nikolaychebotov&button_colour=ff8614&font_colour=000000&font_family=Bree&outline_colour=000000&coffee_colour=FFDD00">
                </a>
                <strong style="margin-left:10px;" class="subheading">Оставайтесь на связи со мной в социальных сетях!</strong>
                <v-spacer></v-spacer>
                <v-btn v-for="(icon, i) in socialIcons"
                       :key="i"
                       :href="icon.profile_url"
                       dark
                       icon
                       target="_blank"
                       style="margin-left: 30px;">
                    <v-icon size="30px" v-text="">{{ icon.icon_name }}</v-icon>
                </v-btn>
            </v-card-title>
        </v-card>

        <v-footer height="auto"
                  color="orange darken-3">
            <v-layout row wrap>
                <v-flex class="attribution"
                        text-xs-center
                        text-sm-left
                        white--text
                        xs12
                        sm6
                        pl-3>
                    Сделано с <v-icon small color="red lighten-1">mdi-heart</v-icon> Чеботовым Николаем <a href="https://unchase.ru" target="_blank">(Unchase)</a> с использованием <a href="https://vuetifyjs.com?ref=unchase" target="_blank">Vuetify</a> и <a href="https://statiq.dev/" target="_blank">Statiq</a>
                </v-flex>
                <v-flex class="attribution"
                        text-xs-center
                        text-sm-right
                        white--text
                        xs12
                        sm6
                        pr-3>
                    Copyright © <a href="https://unchase.ru" target="_blank">Unchase</a> {{ getCurrentYear }} Все права защищены
                </v-flex>
            </v-layout>
        </v-footer>
    </div>
</template>

<script>
    module.exports = {
        data: () => ({
            socialIcons: [
                { icon_name: 'fab fa-github-square', title: 'GitHub.com', profile_url: 'https://github.com/unchase' },
                { icon_name: 'fab fa-medium', title: 'Medium.com', profile_url: 'https://medium.com/@unchase' },
                { icon_name: 'fab fa-dev', title: 'Dev.to', profile_url: 'https://dev.to/unchase' },
                { icon_name: 'fab fa-twitter-square', title: 'Twitter.com', profile_url: 'https://twitter.com/unchase12' },
                { icon_name: 'fab fa-facebook-square', title: 'Facebook.com', profile_url: 'https://www.facebook.com/unchase' },
                { icon_name: 'fab fa-hire-a-helper', title: 'Habr.com', profile_url: 'https://habr.com/ru/users/unchase' }
            ],
            links: [
                { title: 'Принять участие', url: '/get-involved', icon: 'mdi-source-pull' },
                { title: 'Предложить', url: '/suggest', icon: 'mdi-plus-box' },
                { title: 'API', url: '/api', icon: 'mdi-api' }
            ]
        }),
        props: {
            description: {
                type: String,
                required: false,
                default: 'Тестовое описание'
            }
        },
        computed: {
            getCurrentYear() {
                return (new Date()).getFullYear();
            }
        }
    }
</script>