<template>
  <v-app id="inspire">
    <v-system-bar app>
      <v-spacer></v-spacer>

      <v-icon>mdi-square</v-icon>

      <v-icon>mdi-circle</v-icon>

      <v-icon>mdi-triangle</v-icon>
    </v-system-bar>

    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title> PAGINA CONTROL...</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer
        v-model="drawer"
        fixed
        temporary
        
      >
    <v-card
        class="mx-auto"
        width="300"
      >
        <v-list>
          <v-list-item
          to="Home">
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
    
            <v-list-item-title>Inicio</v-list-item-title>
          </v-list-item>

          <v-list-item
          to="Login">
            <v-list-item-icon>
              <v-icon>mdi-login-variant</v-icon>
            </v-list-item-icon>
    
            <v-list-item-title>Log in</v-list-item-title>
          </v-list-item>


          <v-list-group
            :value="true"
            prepend-icon="mdi-account-circle"
          >
            <template v-slot:activator>
              <v-list-item-title>Users</v-list-item-title>
            </template>
    
            <v-list-group
              :value="true"
              no-action
              sub-group
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Admin</v-list-item-title>
                </v-list-item-content>
              </template>
    
              <v-list-item
                v-for="([title, icon], i) in admins"
                :key="i"
                link
              >
                <v-list-item-title v-text="title"></v-list-item-title>
    
                <v-list-item-icon>
                  <v-icon v-text="icon"></v-icon>
                </v-list-item-icon>
              </v-list-item>
            </v-list-group>
    
            <v-list-group
              no-action
              sub-group
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Opciones</v-list-item-title>
                </v-list-item-content>
              </template>
    
              <v-list-item
                v-for="([title, icon, ruta], i) in cruds"
                :key="i"
                :to="ruta"
                link
              >
                <v-list-item-title v-text="title"></v-list-item-title>
    
                <v-list-item-icon>
                  <v-icon v-text="icon"></v-icon>
                </v-list-item-icon>
              </v-list-item>
            </v-list-group>
          </v-list-group>
        </v-list>
      </v-card>
     </v-navigation-drawer>

    <v-main class="grey lighten-2">
      <v-container fluid>
      <router-view></router-view>
      </v-container>
      
     </v-main>
  </v-app>

</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    drawer:null,
    admins: [
      ['Management', 'mdi-account-multiple-outline'],
      ['Settings', 'mdi-cog-outline'],
    ],
    cruds: [
      ['Articulo', 'mdi-plus-outline','Articulos'],
      ['Categoria', 'mdi-file-outline','Categorias'],
    ],
  })
  };

</script>