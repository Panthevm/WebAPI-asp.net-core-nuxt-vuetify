<template>
  <v-app white>
    <v-navigation-drawer v-model="drawer" fixed temporary app>
      <v-list>
        <v-list-tile router :to="item.to" :key="i" v-for="(item, i) in items" exact>
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-group no-action sub-group value="true">
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Товары</v-list-tile-title>
            </v-list-tile>
          </template>
          <v-list-tile router :to="categ.to" v-for="(categ, i) in category" :key="i">
            <v-list-tile-title v-text="categ.title"></v-list-tile-title>
            <v-list-tile-action>
              <v-icon v-html="categ.icon"></v-icon>
            </v-list-tile-action>
          </v-list-tile>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-toolbar fixed app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
    </v-toolbar>

    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

    <v-footer height="auto">
      <v-layout justify-center row wrap>
        <v-btn v-bind:href="item.href" v-for="(item, i) in social" :key="i" flat round>
          <v-title v-text="item.title"></v-title>
        </v-btn>
        <v-flex py-3 text-xs-center xs12>
          &copy;2019 —
          <strong>Marsell</strong>
        </v-flex>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      category: [
        { icon: 'apps', title: 'Кровати', to: '/' },
        { icon: 'apps', title: 'Комоды', to: '/inspire' },
        { icon: 'apps', title: 'Шкафы', to: '/@' }
      ],
      items: [
        { icon: 'apps', title: 'Главаня страница', to: '/' }
      ],
      social: [
        { title: 'Инстраграм', href: 'https://vk.com/id391422246' },
        { title: 'Вконтакте', href: 'https://vk.com/id391422246' }
      ],
      title: 'MARSELL'
    }
  }
}
</script>
