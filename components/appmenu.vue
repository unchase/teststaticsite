<template>
    <nav class="green lighten-1">
        <div class="nav-wrapper container">
            <div class="col s12">
                <router-link to="/" class="brand-logo">
                    <div class="logo-header text-center">
                        <div class="logo container-fluid layout-container">
                            <a href="/"><img src="/assets/logo.svg"></img>Awesome Russian IT</a>
                        </div>
                    </div>
                </router-link>
                <ul id="nav-mobile" class="right hide-on-med-and-down">
                    <li><router-link to="/">Домашняя</router-link></li>
                    <li><router-link to="/events">События</router-link></li>
                    <li><router-link to="/podcasts">Подкасты</router-link></li>
                    <li><router-link to="/blogs">Блоги</router-link></li>
                    <li><router-link to="/channels">Каналы</router-link></li>
                    <!--<li><router-link to="/about">О программе</router-link></li>
                    <li><router-link to="/contacts">Контакты</router-link></li>
                    <li><router-link to="/404">404</router-link></li>-->
                </ul>
            </div>
        </div>
    </nav>
</template>

<!--<div class="logo-header text-center">
    <div class="logo container-fluid layout-container">
        <a href="/"><img src="/assets/logo.svg"></img></a>
        <p class="d-none d-sm-block">Awesome .NET open source & community resources</p>
    </div>
</div>-->