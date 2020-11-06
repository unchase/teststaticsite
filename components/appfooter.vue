<template>
    <!--<footer class="page-footer green lighten-1">
        <div class="container">
            <div class="row">
                <div class="col l6 s12">
                    <h5 class="white-text">О приложении</h5>
                    <p class="grey-text text-lighten-4">{{ description }}</p>
                </div>
                <div class="col l4 offset-l2 s12">
                    <h5 class="white-text">Ссылки</h5>
                    <ul>
                        <li><router-link class="grey-text text-lighten-3" to="/">Домашняя</router-link></li>
                        <li><router-link class="grey-text text-lighten-3" to="/events">События</router-link></li>
                        <li><router-link class="grey-text text-lighten-3" to="/podcasts">Подкасты</router-link></li>
                        <li><router-link class="grey-text text-lighten-3" to="/blogs">Блоги</router-link></li>
                        <li><router-link class="grey-text text-lighten-3" to="/channels">Каналы</router-link></li>-->
    <!--<li><router-link class="grey-text text-lighten-3" to="/about">О программе</router-link></li>
    <li><router-link class="grey-text text-lighten-3" to="/contacts">Контакты</router-link></li>-->
    <!--</ul>
                </div>
            </div>
        </div>
        <div class="footer-copyright">
            <div class="container">
                © 2020 Unchase - Все права защищены
                <a class="grey-text text-lighten-4 right" href="#!">Больше ссылок</a>
            </div>
        </div>
    </footer>-->


    <div>
        <v-card class="flex"
                flat
                tile>
            <v-card-title class="orange darken-2 white--text">
                <!--<v-btn icon>
        <v-icon size="24px" v-text=""></v-icon>
    </v-btn>-->
                <a href="https://www.buymeacoffee.com/nikolaychebotov" target="_blank">
                    <img src="https://img.buymeacoffee.com/button-api/?text=Support me!&emoji=🙏&slug=nikolaychebotov&button_colour=ff8614&font_colour=000000&font_family=Bree&outline_colour=000000&coffee_colour=FFDD00">
                </a>
                <strong style="margin-left:10px;" class="subheading">Оставайтесь на связи со мной в социальных сетях!</strong>


                <v-btn v-for="(link, j) in links"
                       :key="j"
                       :href="link.url"
                       dark
                       icon
                       style="margin-left: 10px;">
                    <v-icon size="30px" :v-text="link.title"></v-icon>
                </v-btn>


                <!--<a style="margin-left:10px;" href="/get-involved">
                    <div>Принять участие</div>
                </a>
                <a style="margin-left:10px;" href="/suggest">
                    <div>Предложить</div>
                </a>
                <a style="margin-left:10px;" href="/api">
                    <div>API</div>
                </a>-->
                <v-spacer></v-spacer>
                <!--<v-btn dark icon href="https://medium.com/@unchase" target="_blank">
        <v-icon size="24px" v-text="">fab fa-medium</v-icon>
    </v-btn>-->
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
                { icon_name: 'fab fa-hire-a-helper', title: 'Habr.com', profile_url: 'https://habr.com/ru/users/unchase' }
            ],
            links: [
                { title: 'Принять участие', url: '/get-involved' },
                { title: 'Предложить', url: '/suggest' }
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