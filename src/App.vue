<template>
  <v-app id="keep">
    <v-app-bar
      app
      clipped-left
      color="amber"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <span class="title ml-3 mr-5">ТСЖ&nbsp;<span class="font-weight-light">БЕСПЛАТНОЕ</span></span>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Поиск по CRM"
      />

      <v-spacer />
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      color="grey lighten-4"
    >
      <v-list
        dense
        class="grey lighten-4"
      >
        <template >

          <v-list-item v-for="item in items" :key="item.i" router :to="item.route">
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="grey--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>



<script>

 
  export default {
    name: 'App',
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      items: [
        { 
          icon: 'waves', 
          text: 'Счетчики',
          route: '/counts'
        },
        { 
          icon: 'people_outline', 
          text: 'Жители',
          route: '/inhabitans'
        },
        { 
          icon: 'people_alt', 
          text: 'Сотрудники',
          route: '/employee' 
        },

        { 
          icon: 'copyright', 
          text: 'Блог',
          route: '/blog'
        },

        { 
          icon: 'email', 
          text: 'Сообщения',
          route: '/messages'
        },

        { 
          icon: 'account_tree', 
          text: 'Настройки',
          route: '/settings'
          },
      ],
    }),
  }
</script>
<style scoped>
#keep .v-navigation-drawer__border {
  display: none
}
</style>

