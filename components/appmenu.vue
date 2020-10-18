<template>
    <nav class="green lighten-1">
        <div class="nav-wrapper container">
            <div class="col s12">
                <router-link to="/" class="brand-logo">Awesome Russian IT</router-link>
                <ul id="nav-mobile" class="right hide-on-med-and-down">
                    <li><router-link to="/">Домашняя</router-link></li>
                    <li><router-link to="/events">События</router-link></li>
                    <li><router-link to="/podcasts">Подкасты</router-link></li>
                    <li><router-link to="/blogs">Блоги</router-link></li>
                    <li><router-link to="/channels">Каналы</router-link></li>
                    <!--<li><search-box :project-keys="projectKeys"></search-box></li>-->
                    <!--<li><router-link to="/about">О программе</router-link></li>
                    <li><router-link to="/contacts">Контакты</router-link></li>
                    <li><router-link to="/404">404</router-link></li>-->
                </ul>
            </div>
        </div>
    </nav>
</template>