<template>
    <nav>
        <v-navigation-drawer 
            v-model="drawer"
            clipped
            class="grey lighten-4"
            app
        >
            <v-list
                dense
                class="grey lighten-4"
            >
                <template v-for="(item, i) in items">
                    <v-layout
                        v-if="item.heading"
                        :key="i"
                        row
                        align-center
                    >
                        <v-flex xs6>
                            <v-subheader>
                                {{ item.heading }}
                            </v-subheader>
                        </v-flex>
                    </v-layout>

                    <v-divider
                        v-else-if="item.divider"
                        :key="i"
                        dark
                        class="my-3"
                    ></v-divider>

                    <v-list-tile
                        v-else
                        :key="i"
                        :to="item.path"
                    >
                        <v-list-tile-action>
                            <v-icon>{{ item.icon }}</v-icon>
                        </v-list-tile-action>
                        <v-list-tile-content>
                            <v-list-tile-title>
                                {{ item.text }}
                            </v-list-tile-title>
                        </v-list-tile-content>
                    </v-list-tile>
                </template>
            </v-list>
        </v-navigation-drawer>

        <v-toolbar 
            dark
            fixed
            clipped-left
            app
            color="primary"
        >
            <v-toolbar-side-icon
                
                @click="drawer = !drawer"
            >
            </v-toolbar-side-icon>

            <v-img
                src="https://cdn1.iconfinder.com/data/icons/dotted-charts/512/links_diagram-128.png"
                max-height="38px"
                max-width="38px"
                v-on:click="goTo('/')"
                :style="{ cursor: 'pointer'}"
            >
            </v-img>

            <v-toolbar-title>
                <span>CLAV</span>
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <v-toolbar-items>
                <v-btn @click="goBack" flat>
                    <v-icon dark left>arrow_back</v-icon>Back
                </v-btn>
            </v-toolbar-items>
        </v-toolbar>
    </nav>
</template>

<script>
export default {
    name: 'NavBar',
    data() {
        return {
            drawer: false, // this.$vuetify.breakpoint.lgAndUp,
            items: [
                { heading: 'Consulta' },
                { text: 'Lista Consolidada', path: '/classes', icon: 'mdi-file-tree' },
                { text: 'Entidades', path: '/entidades', icon: 'mdi-account-group' },
                { text: 'Tipologias', path: '/tipologias', icon: 'mdi-view-list' },
                { text: 'Legislação', path: '/legislacao', icon: 'mdi-book' },
                { divider: true }
            ]
        }
    },
    methods:{
        goBack : function(){
            this.$router.go(-1)
        },
        goTo : function (path) {
            this.$router.push(path)
        }
    }
}
</script>
