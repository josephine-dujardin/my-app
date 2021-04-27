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
        <v-list-item class="mt-4 px-2">
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
          class="mt-4"
          >Nous sélectionnons pour vous les meilleurs installateurs de panneaux solaires partout en France. Découvrez les artisans de votre département en un click.</v-list-item>
          <div id="app">
            <v-app id="inspire">
              <v-card
                v-if="!mini"
                class="mx-2 mt-8 overflow-y-auto"
                max-width="450"
                max-height="600"
              >
                <v-system-bar></v-system-bar>
            
                <v-toolbar
                  flat
                  color="transparent"
                >
                  <v-btn icon>
                    <v-icon>mdi-arrow-left</v-icon>
                  </v-btn>
            
                  <v-text-field
                    v-model="search"
                    append-icon="mdi-magnify"
                    label="Saisissez votre département"
                    single-line
                  ></v-text-field>
                </v-toolbar>            
                <v-card-text class="py-0">
                </v-card-text>            
                <v-list three-line>
                  <v-list-item
                    v-for="(item, i) in searching"
                    :key="i"
                    ripple
                    @click="() => {}"
                  >            
                    <v-list-item-content>
                      <span
                        class="text-uppercase font-weight-regular caption"
                        v-text="item.category"
                      ></span>            
                      <div v-text="item.title"></div>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-app>
          </div>
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
        drawer: true,
        group: null,
        items: [
      {
        category: "2A",
        title: "Corse-du-Sud",

      },
      {        
        category: "2B",
        title: "Haute-Corse",
      },
      {       
        category: "01",
        title: "Ain",
      },
      {       
        category: "02",
        title: "Aisne",
      },
      {        
        category: "03",
        title: "Allier",
      },
      {
        category: "04",
        title: "Alpes-de-Haute Provence",
      },
      {
        category: "05",
        title: "Hautes-Alpes",
      },
      {
        category: "06",
        title: "Alpes Maritimes",
      },
      {
        category: "07",
        title: "Ard\u00e8che",
      },
      {
        category: "08",
        title: "Ardennes",
      },
      {
        category: "09",
        title: "Ari\u00e8ge",
      },
      {
        category: "10",
        title: "Aube",
      },
      {
        category: "11",
        title: "Aude",
      },
      {
        category: "12",
        title: "Aveyron",
      },
      {
        category: "13",
        title: "Bouches-du-Rh\u00f4ne",
      },
      {
        category: "14",
        title: "Calvados",
      },
      {
        category: "15",
        title: "Cantal",
      },
      {
        category: "16",
        title: "Charente",
      },
      {
        category: "17",
        title: "Charente-Maritime",
      },
      {
        category: "18",
        title: "Cher",
      },
      {
        category: "19",
        title: "Corr\u00e8ze",
      },
      {
        category: "20",
        title: "Corse",
      },
      {
        category: "21",
        title: "C\u00f4te d'Or",
      },
      {
        category: "22",
        title: "C\u00f4tes d'Armor",
      },
      {
        category: "23",
        title: "Creuse",
      },
      {
        category: "24",
        title: "Dordogne",
      },
      {
        category: "25",
        title: "Doubs",
      },
      {
        category: "26",
        title: "Dr\u00f4me",
      },
      {
        category: "27",
        title: "Eure",
      },
      {
        category: "28",
        title: "Eure-et-Loire",
      },
      {
        category: "29",
        title: "Finist\u00e8re",
      },

      {
        category: "30",
        title: "Gard",
      },
      {
        category: "31",
        title: "Haute-Garonne",
      },
      {
        category: "32",
        title: "Gers",
      },
      {
        category: "33",
        title: "Gironde",
      },
      {
        category: "34",
        title: "H\u00e9rault",
      },
      {
        category: "35",
        title: "Ille-et-Vilaine",
      },
      {
        category: "36",
        title: "Indre",
      },
      {
        category: "37",
        title: "Indre-et-Loire",
      },
      {
        category: "38",
        title: "Is\u00e8re",
      },
      {
        category: "39",
        title: "Jura",
      },
      {
        category: "40",
        title: "Landes",
      },
      {
        category: "41",
        title: "Loir-et-Cher",
      },
      {
        category: "42",
        title: "Loire",
      },
      {
        category: "43",
        title: "Haute-Loire",
      },
      {
        category: "44",
        title: "Loire-Atlantique",
      },
      {
        category: "45",
        title: "Loiret",
      },
      {
        category: "46",
        title: "Lot",
      },
      {
        category: "47",
        title: "Lot-et-Garonne",
      },
      {
        category: "48",
        title: "Loz\u00e8re",
      },
      {
        category: "49",
        title: "Maine-et-Loire",
      },
      {
        category: "50",
        title: "Manche",
      },
      {
        category: "51",
        title: "Marne",
      },
      {
        category: "52",
        title: "Haute-Marne",
      },
      {
        category: "53",
        title: "Mayenne",
      },
      {
        category: "54",
        title: "Meurthe-et-Moselle",
      },
      {
        category: "55",
        title: "Meuse",
      },
      {
        category: "56",
        title: "Morbihan",
      },
      {
        category: "57",
        title: "Moselle",
      },
      {
        category: "58",
        title: "Ni\u00e8vre",
      },
      {
        category: "59",
        title: "Nord",
      },
      {
        category: "60",
        title: "Oise",
      },
      {
        category: "61",
        title: "Orne",
      },
      {
        category: "62",
        title: "Pas-de-Calais",
      },
      {
        category: "63",
        title: "Puy-de-D\u00f4me",
      },
      {
        category: "64",
        title: "Pyren\u00e9es-Atlantiques",
      },
      {
        category: "65",
        title: "Hautes-Pyren\u00e9es",
      },
      {
        category: "66",
        title: "Pyren\u00e9es-Orientales",
      },
      {
        category: "67",
        title: "Bas-Rhin",
      },
      {
        category: "68",
        title: "Haut-Rhin",
      },
      {
        category: "69",
        title: "Rh\u00f4ne",
      },
      {
        category: "70",
        title: "Haute-Sa\u00f4ne",
      },
      {
        category: "71",
        title: "Sa\u00f4ne-et-Loire",
      },
      {
        category: "72",
        title: "Sarthe",
      },
      {
        category: "73",
        title: "Savoie",
      },
      {
        category: "74",
        title: "Haute-Savoie",
      },
      {
        category: "75",
        title: "Paris",
      },
      {
        category: "76",
        title:"Seine-Maritime",
      },
      {
        category: "77",
        title: "Seine-et-Marne",
      },
      {
        category: "78",
        title: "Yvelines",
      },
      {
        category: "79",
        title: "Deux-S\u00e8vres",
      },
      {
        category: "80",
        title: "Somme",
      },
      {
        category: "81",
        title: "Tarn",
      },
      {
        category: "82",
        title: "Tarn-et-Garonne",
      },
      {
        category: "83",
        title:  "Var",
      },
      {
        category: "84",
        title:"Vaucluse",
      },
      {
        category: "85",
        title:  "Vend\u00e9e",
      },
      {
        category: "86",
        title: "Vienne",
      },
      {
        category: "87",
        title:  "Haute-Vienne",
      },
      {
        category: "88",
        title: "Vosges",
      },
      {
        category: "89",
        title:  "Yonne",
      },
      {
        category: "90",
        title: "Territoire de Belfort",
      },
      {
        category: "91",
        title: "Essonne",
      },
      {
        category: "92",
        title:  "Hauts-de-Seine",
      },
      {
        category: "93",
        title: "Seine-Saint-Denis",
      },
      {
        category: "94",
        title:  "Val-de-Marne",
      },
      {
        category: "95",
        title: "Val-d'Oise",
      },
      ],
        search: '',
  
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
  
  computed: {
    keywords () {
      if (!this.search) return []

      const keywords = []

      for (const search of this.searching) {
        keywords.push(search.keyword)
      }

      return keywords
    },
    searching () {
      if (!this.search) return this.items

      const search = this.search.toLowerCase()

      return this.items.filter(item => {
        const text = item.title.toLowerCase()

        return text.indexOf(search) > -1
      })
    },
  },
}
</script>