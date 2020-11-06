<template>
    <v-toolbar color="orange darken-2"
               dark
               flat
               max-height="120">
        <v-icon large left>
            mdi-monitor-star
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
            <v-tabs centered v-model="active_tab" optional hide-slider>
                <v-tab v-for="tab of tabs" :key="tab.id" :href="tab.url">
                    {{tab.name}}
                </v-tab>
            </v-tabs>
        </template>
    </v-toolbar>
</template>

<script>
    module.exports = {
        data: () => ({
            active_tab: 1,
            tabs: [
                { id: 1, name: 'Домашняя', url: '/' },
                { id: 2, name: 'События', url: '/events' },
                { id: 3, name: 'Подкасты', url: '/podcasts' },
                { id: 4, name: 'Каналы', url: '/channels' },
                { id: 5, name: 'Блоги', url: '/blogs' }
            ]
        }),
        props: {
            title: {
                type: String,
                required: false,
                default: 'Awesome Russian IT'
            }
        }
    }
</script>