<template>
  <div id="app">
    <v-app>
      <v-toolbar app>
        <v-icon large left>mdi-chart-line</v-icon>
        <v-toolbar-title>LMS keretrendszerek az iskolarendszerű szakképzésben - kérdőív</v-toolbar-title>
        <v-spacer/>
      </v-toolbar>
      <v-content>
        <v-container fluid>
          <v-layout row wrap justify-center>
            <!-- 1. Melyik megyében/megyékben található az intézmény? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>place</v-icon>
                    <span>1. Melyik megyében/megyékben található az intézmény?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    dark
                    :items="megyekLista"
                    clearable
                    chips
                    multiple
                    label="Megye:"
                    outline
                    v-model="megyek"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 2. Tanulók száma a nappali tagozaton -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>school</v-icon>
                    <span>2. Tanulók száma a nappali tagozaton</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    :items="tanulokSzamaLista"
                    suffix="fő"
                    clearable
                    label="Tanulók száma"
                    outline
                    v-model="tanulokSzama"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 3. Főállású tanárok / szakoktatók száma az intézményben -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>people</v-icon>
                    <span>3. Főállású tanárok / szakoktatók száma az intézményben</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    :items="tanarokSzamaLista"
                    suffix="fő"
                    clearable
                    label="Tanárok száma"
                    outline
                    v-model="tanarokSzama"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 4. Főállású rendszergazdák száma -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>supervisor_account</v-icon>
                    <span>4. Főállású rendszergazdák száma</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    :items="rendszergazdakSzamaLista"
                    suffix="fő"
                    clearable
                    label="Rendszergazdák száma"
                    outline
                    v-model="rendszergazdakSzama"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 5. Internet kapcsolat letöltési sávszélessége -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>cloud_download</v-icon>
                    <span>5. Internet kapcsolat letöltési sávszélessége</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-text-field
                    type="text"
                    suffix="Mbit/sec"
                    v-model="letoltesiSebesseg"
                    label="Sávszélesség"
                    mask="#######"
                    clearable
                    outline
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 6. Tanulók által használt, LAN hálózatba kötött számítógépek száma -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>desktop_mac</v-icon>
                    <span>6. Tanulók által használt, LAN hálózatba kötött számítógépek száma</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-text-field
                    type="text"
                    suffix="darab"
                    v-model="szamitogepekSzama"
                    label="Számítógépek száma"
                    mask="#######"
                    clearable
                    outline
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 7. Saját telepítésű LMS keretrendszer telepítéséhez és üzemeltetésre rendelkeznek megfelelően képzett szakemberrel -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>how_to_reg</v-icon>
                    <span>7. Saját telepítésű LMS keretrendszer telepítéséhez és üzemeltetésre rendelkeznek megfelelően képzett szakemberrel</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select :items="igenNem" clearable label="Szakember" outline v-model="lmsEE"/>
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 8. Saját telepítésű LMS keretrendszer üzemeltetésre rendelkeznek megfelelő hardver eszközökkel? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>cloud_done</v-icon>
                    <span>8. Saját telepítésű LMS keretrendszer üzemeltetésre rendelkeznek megfelelő hardver eszközökkel?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    :items="igenNem"
                    clearable
                    label="Megfelelő eszközpark"
                    outline
                    v-model="lmsHW"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-content>
      <v-footer/>
    </v-app>
  </div>
</template>

<script  lang="ts">
import { Component, Vue } from "vue-property-decorator";
import firebase, { storage } from "firebase";
import db from "@/firebaseApp";

@Component({
  firestore: {
    locations: db.collection("answers")
  }
})
export default class App extends Vue {
  private megyekLista: string[] = [
    "Budapest",
    "Bács-Kiskun megye",
    "Baranya megye",
    "Békés megye",
    "Borsod-Abaúj-Zemplén megye",
    "Csongrád megye",
    "Fejér megye",
    "Győr-Moson-Sopron megye",
    "Hajdú-Bihar megye",
    "Heves megye",
    "Jász-Nagykun-Szolnok megye",
    "Komárom-Esztergom megye",
    "Nógrád megye",
    "Pest megye",
    "Somogy megye",
    "Szabolcs-Szatmár-Bereg megye",
    "Tolna megye megye",
    "Vas megye",
    "Veszprém megye",
    "Zala megye"
  ];

  private tanulokSzamaLista: string[] = [
    "1-50",
    "51-100",
    "101-150",
    "151-200",
    "201-500",
    "501-1000",
    "1001-2000",
    "2001-"
  ];

  private tanarokSzamaLista: string[] = [
    "1-40",
    "41-80",
    "81-120",
    "121-150",
    "151-200",
    "200-"
  ];

  private igenNem: string[] = ["Igen", "Nem"];

  private rendszergazdakSzamaLista: string[] = ["0", "1", "2", "3-"];

  private megyek: string[] = [];
  private tanulokSzama: string = "";
  private tanarokSzama: string = "";
  private rendszergazdakSzama: string = "";
  private letoltesiSebesseg: string = "";
  private szamitogepekSzama: string = "";
  private lmsEE: string = "";
  private lmsHW: string = "";
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  background-color: #eeeeee;
}
.myLink {
  text-decoration: none;
}
.floatleft {
  float: left;
}
</style>
