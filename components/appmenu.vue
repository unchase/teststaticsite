<template>
    <header class="mb-4 green lighten-1">
    <div class="logo-header text-center">
        <div class="logo container-fluid layout-container">
            <a href="/"><img src="/assets/logo.svg"></img></a>
            <p class="d-none d-sm-block">Awesome .NET open source & community resources</p>
        </div>
    </div>
    <b-navbar toggleable="md" type="dark" variant="dark" class="font-weight-bold">
        <b-container fluid class="layout-container">
            <div class="flex-grow-1">
                <b-navbar-toggle target="main-nav-collapse"></b-navbar-toggle>
                <b-collapse is-nav id="main-nav-collapse">
                    <b-navbar-nav class="float-md-right">
                        <b-nav-item href="/">Домашняя</b-nav-item>
                        <b-nav-item href="/events">События</b-nav-item>
                        <b-nav-item href="/podcasts">Подкасты</b-nav-item>
                        <b-nav-item href="/blogs">Блоги</b-nav-item>
                        <b-nav-item href="/channels">Каналы</b-nav-item>
                    </b-navbar-nav>
                </b-collapse>
            </div>
            <!--<b-navbar-nav class="align-self-start">
                <search-box :project-keys="projectKeys"></search-box>
            </b-navbar-nav>-->
        </b-container>
    </b-navbar>
</header>
</template>

<!--<div class="logo-header text-center">
    <div class="logo container-fluid layout-container">
        <a href="/"><img src="/assets/logo.svg"></img></a>
        <p class="d-none d-sm-block">Awesome .NET open source & community resources</p>
    </div>
</div>-->