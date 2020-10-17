<template>
    <footer class="page-footer green lighten-1">
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
                        <li><router-link class="grey-text text-lighten-3" to="/channels">Каналы</router-link></li>
                        <!--<li><router-link class="grey-text text-lighten-3" to="/about">О программе</router-link></li>
                        <li><router-link class="grey-text text-lighten-3" to="/contacts">Контакты</router-link></li>-->
                    </ul>
                </div>
            </div>
        </div>
        <div class="footer-copyright">
            <div class="container">
                © 2020 Unchase - Все права защищены
                <a class="grey-text text-lighten-4 right" href="#!">Больше ссылок</a>
            </div>
        </div>
    </footer>
</template>

<script>
    module.exports = {
        props: {
            description: {
                type: String,
                required: false,
                default: 'Тестовое описание'
            }
        }
    }
</script>