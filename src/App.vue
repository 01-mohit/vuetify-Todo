 <template>
  <v-app id="inspire" v-cloak>
    <v-navigation-drawer v-model="drawer" app color="cyan lighten-2">
      
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Vuetify Todo
          </v-list-item-title>
          <v-list-item-subtitle>
            Todo list!
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <footer id="footer" class="ml-7">
        © Copyright H.MOHIT 2021
      </footer>
    </v-navigation-drawer>

    
    <v-app-bar
      app
      color="primary"
      dark
      src="intel.jpg"
      shrink-on-scroll
    >
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Todo List</v-toolbar-title>

      <v-spacer></v-spacer>

      <!-- <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn> -->
    </v-app-bar>
    

    <v-main>
            <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ 
      drawer: null, 
      items: [
          { title: 'Todo', icon: 'mdi-format-list-checks' , to: '/' },
          { title: 'About', icon: 'mdi-help-box' , to: '/about'},
        ],
      }),
  }
</script>
<style scoped>
#footer{
 position:fixed;
 bottom:0;
 align-items: center;
 text-align: center;
 color: black;
 margin-left: 2;
}
</style>