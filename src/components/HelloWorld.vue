<template>
  <v-card 
    class="d-flex-column"
    height="100%"
    width="100vw"
  >
    <v-app-bar
      color="grey lighten-3"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Elance</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      bottom
      temporary      
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="grey lighten-3"
        >
          <v-list-item>
            <v-list-item-title>Votre compte</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Guide Complet Solaire 2021</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Passage à l'électricité solaire</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Juridique</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-div>
          <v-navigation-drawer
            v-model="drawer"
            :mini-variant.sync="mini"
            permanent
                class="d-flex-column"
                height="92%"
                width="400px" 
          >
          <v-list-item class="px-2">
            <v-list-item-avatar>
              <v-img src="https://www.vhv.rs/dpng/d/441-4412135_egypt-sun-icon-clipart-png-download-clip-art.png"></v-img>
            </v-list-item-avatar>

            <v-list-item-title><strong>Les installateurs près de chez moi</strong></v-list-item-title>
            
            <v-btn
              icon
              @click.stop="mini = !mini"
            >
              <v-icon>mdi-chevron-left</v-icon>              
            </v-btn>            
          </v-list-item>
          <v-list-item
          v-if="!mini"
          class=""
          >Nous sélectionnons pour vous les meilleurs installateurs de panneaux solaires partout en France. Découvrez les artisans de votre département en un click.</v-list-item>
          <v-text-field
            v-if="!mini"
            class="px-4"
            label="Saisissez votre département"
            :rules="rules"
            hide-details="auto"
          ></v-text-field>
        </v-navigation-drawer>
        <v-footer
          dark
          padless          
        >
        <v-card
          flat
          tile
          width="100vw"
          class="black white--text text-center"
        >
          <v-card-text>
            <v-btn
              v-for="icon in icons"
              :key="icon"
              class="mx-4 white--text"
              icon
            >
              <v-icon size="24px">
                {{ icon }}
              </v-icon>
            </v-btn>
          </v-card-text>

          <v-card-text class="white--text pt-0">
            service@maison-elance.com <tr/>
            Mentions Légales - Déclaration de Confidentialité - Conditions Générales de Services
          </v-card-text>

          <v-divider></v-divider>

          <v-card-text class="white--text">
            <strong>Copyright @ 2020 élance Technologies Propres S.A.S Tous droits réservés.</strong>
          </v-card-text>
        </v-card>
      </v-footer>
    </v-div>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
        drawer: false,
        group: null,
        icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
        rules: [
        value => !!value || 'Required.',
        value => (value && value.length >= 3) || 'Min 3 characters',
      ],
        mini: false,
        }),
        watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>