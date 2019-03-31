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
            <!-- Bevezető -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>mdi-information-outline</v-icon>
                    <span>
                      Tisztelt Igazgat Úr! Kedves Kolléga!
                      <br>A BME GTK Alkalmazott Pedagógia és Pszichológia
                      Intézet Műszaki Pedagógia Tanszék Közoktatási Vezető és pedagógus-szakvizsga szakirányú továbbképzési
                      szak végzős hallgatójaként készítem szakdolgozatomat.
                      <br>A dolgozat címe:
                      <br>
                      <b>E-learning keretrendszerek alkalmazása az iskolarendszerű szakképzésben</b>
                      <br>Kérem, hogy a következő kérdőív kitöltésével segítse kutatásomat!
                      <br>Köszönettel: Nits László
                    </span>
                  </div>
                </v-card-title>
              </v-card>
            </v-flex>

            <!-- 1. Melyik megyében / megyékben található az intézmény? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>place</v-icon>
                    <span>1. Melyik megyében / megyékben található az intézmény?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    dark
                    :items="megyekLista"
                    clearable
                    chips
                    multiple
                    label="Megye"
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
                    <v-icon class="floatleft" large left>group_add</v-icon>
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
            <!-- 3. Fő állású tanárok / szakoktatók száma az intézményben -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>person</v-icon>
                    <span>3. Fő állású tanárok / szakoktatók száma az intézményben</span>
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
                    <v-icon class="floatleft" large left>person_add</v-icon>
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
                  <v-select
                    :items="tanuloiSzamitogepekLanLista"
                    suffix="db"
                    clearable
                    label="Számítógépek száma"
                    outline
                    v-model="szamitogepekSzama"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 7. Saját telepítésű e-learning (LMS) keretrendszer telepítéséhez és üzemeltetésre rendelkeznek megfelelően képzett szakemberrel? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon large left>mdi-account-question</v-icon>
                    <span>7. Saját telepítésű e-learning (LMS) keretrendszer telepítéséhez és üzemeltetésre rendelkeznek megfelelően képzett szakemberrel?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-switch
                    color="success"
                    class="bordered pl-4 pt-4"
                    v-model="lmsEE"
                    :label="`${lmsEE ? 'Igen' : 'Nem'}`"
                  ></v-switch>
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 8. Saját telepítésű e-learning (LMS) keretrendszer üzemeltetésre rendelkeznek megfelelő hardvereszközökkel? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon large left>mdi-lan-connect</v-icon>
                    <span>8. Saját telepítésű e-learning (LMS) keretrendszer üzemeltetésre rendelkeznek megfelelő hardvereszközökkel?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-switch
                    color="success"
                    class="bordered pl-4 pt-4"
                    v-model="lmsHW"
                    :label="`${lmsHW ? 'Igen' : 'Nem'}`"
                  ></v-switch>
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 9.	Üzemeltetnek e-learning (LMS) keretrendszert az intézmény LAN hálózatán? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon large left>mdi-auto-fix</v-icon>
                    <span>9. Üzemeltetnek e-learning (LMS) keretrendszert az intézmény LAN hálózatán?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-switch
                    color="success"
                    class="bordered pl-4 pt-4"
                    v-model="lmsLAN"
                    :label="`${lmsLAN ? 'Igen' : 'Nem'}`"
                    @change="lmsValasztott=''; lmsHasznalloTanarok='';"
                  ></v-switch>
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 9.1 Melyik e-learning (LMS) rendszert / rendszereket választották? -->
            <v-flex xs12 sm12 md12 lg12 xl12 v-show="lmsLAN">
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>school</v-icon>
                    <span
                      :class="`${lmsLAN ? '' : 'disabledTitle'}`"
                    >9.1 Melyik e-learning (LMS) rendszert / rendszereket választották?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    dark
                    :items="lmsRendszerekLista"
                    clearable
                    chips
                    :disabled="!lmsLAN"
                    multiple
                    label="LMS"
                    outline
                    v-model="lmsValasztott"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 9.2 A főállású tanárok / szakoktatók közül hányan használják aktívan az iskola hálózatán működő LMS keretrendszert? -->
            <v-flex xs12 sm12 md12 lg12 xl12 v-show="lmsLAN">
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>people</v-icon>
                    <span>9.2 A főállású tanárok / szakoktatók közül hányan használják aktívan az iskola hálózatán működő LMS keretrendszert?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    dark
                    :items="lmsHasznalloTanarokLista"
                    clearable
                    :disabled="!lmsLAN"
                    label="Használók száma"
                    outline
                    v-model="lmsHasznalloTanarok"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 10. Tanárok / szakoktatók használnak NEM saját üzemeltetésű e-learning (LMS) keretrendszert? -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon large left>school</v-icon>
                    <span>10. Tanárok / szakoktatók használnak NEM saját üzemeltetésű e-learning (LMS) keretrendszert?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-switch
                    color="success"
                    class="bordered pl-4 pt-4"
                    v-model="kulsoLMS"
                    :label="`${kulsoLMS ? 'Igen' : 'Nem'}`"
                    @change="kulsoLMSHasznalloTanarok='';"
                  ></v-switch>
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- 10.1  A főállású tanárok / szakoktatók közül hányan használnak aktívan NEM saját üzemeltetésű e-learning (LMS) keretrendszert? -->
            <v-flex xs12 sm12 md12 lg12 xl12 v-show="kulsoLMS">
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>people</v-icon>
                    <span
                      :class="`${kulsoLMS ? '' : 'disabledTitle'}`"
                    >10.1 A főállású tanárok / szakoktatók közül hányan használnak aktívan NEM saját üzemeltetésű e-learning (LMS) keretrendszert?</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-select
                    dark
                    :items="lmsHasznalloTanarokLista"
                    clearable
                    :disabled="!kulsoLMS"
                    label="Használók száma"
                    outline
                    v-model="kulsoLMSHasznalloTanarok"
                  />
                </v-card-actions>
              </v-card>
            </v-flex>
            <!-- MENTÉS -->
            <v-flex xs12 sm12 md12 lg12 xl12>
              <v-card class="mx-auto my-2" color="lightblue" max-width="600" elevation="18" dark>
                <v-img></v-img>
                <v-card-title primary-title>
                  <div>
                    <v-icon class="floatleft" large left>save</v-icon>
                    <span>Mentés</span>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-btn class="mx-auto" dark color="red" @click="add()">Kérdőív adatainak mentése</v-btn>
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
    locations: db.collection("kvk2019")
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

  private lmsRendszerekLista: string[] = [
    "Moodle",
    "CANVAS",
    "Ilias",
    "Blackboard Learn",
    "Sakai",
    "Egyéb"
  ];

  private igenNem: string[] = ["Igen", "Nem"];

  private rendszergazdakSzamaLista: string[] = ["0", "1", "2", "3-"];

  private tanuloiSzamitogepekLanLista: string[] = [
    "-20",
    "21-40",
    "41-60",
    "41-80",
    "81-100",
    "100-150",
    "151-200",
    "201-300",
    "301-400",
    "401-"
  ];

  private lmsHasznalloTanarokLista: string[] = [
    "1-5",
    "6-10",
    "11-20",
    "21-30",
    "31-40",
    "41-50",
    "51-100",
    "101-"
  ];

  private megyek: string[] = []; // 1
  private tanulokSzama: string = ""; // 2
  private tanarokSzama: string = ""; // 3
  private rendszergazdakSzama: string = ""; // 4
  private letoltesiSebesseg: string = "";  // 5
  private szamitogepekSzama: string = ""; // 6
  private lmsEE: boolean = false; // 7
  private lmsHW: boolean = false; // 8
  private lmsLAN: boolean = false; // 9
  private lmsValasztott: string[] = []; // 9.1
  private lmsHasznalloTanarok = ""; // 9.2
  private kulsoLMS: boolean = false; // 10
  private kulsoLMSHasznalloTanarok = ""; // 10.1

  // Új elem hozzáadása az adatbázishoz
  private add(): void {
    let nemAdottVálaszt: string = "";

    if (this.megyek.length === 0) {
      nemAdottVálaszt += "1.  ";
    }
    if (this.tanulokSzama === "") {
      nemAdottVálaszt += "2.  ";
    }
    if (this.tanarokSzama === "") {
      nemAdottVálaszt += "3.  ";
    }
    if (this.rendszergazdakSzama === "") {
      nemAdottVálaszt += "4.  ";
    }
    if (this.letoltesiSebesseg === "") {
      nemAdottVálaszt += "5.  ";
    }
    if (this.szamitogepekSzama === "") {
      nemAdottVálaszt += "6.  ";
    }
    if (nemAdottVálaszt.length > 0) {
      // tslint:disable-next-line:max-line-length
      alert(`A kérdőív adatainak mentéséhez a következő kérdésekre a választ legyen szíves megadni: \r${nemAdottVálaszt}`);
      return;
    }

    if (this.lmsLAN) {
      nemAdottVálaszt = "";
      if (this.lmsValasztott.length === 0) {
        nemAdottVálaszt += "9.1  ";
      }
      if (this.lmsHasznalloTanarok === "") {
        nemAdottVálaszt += "9.2  ";
      }
      if (nemAdottVálaszt.length > 0) {
        // tslint:disable-next-line:max-line-length
        alert(`A kérdőív adatainak mentéséhez a következő kérdésekre a választ legyen szíves megadni: \r${nemAdottVálaszt}`);
        return;
      }
    }

    if (this.kulsoLMS) {
      nemAdottVálaszt = "";
      if (this.kulsoLMSHasznalloTanarok === "") {
        nemAdottVálaszt += "10.1";
      }
      if (nemAdottVálaszt.length > 0) {
        // tslint:disable-next-line:max-line-length
        alert(`A kérdőív adatainak mentéséhez a következő kérdésekre a választ legyen szíves megadni: \r${nemAdottVálaszt}`);
        return;
      }
    }

    const obj = {} as any;
    obj.K00_createdAt = new Date();
    obj.K01_megyek = this.megyek;
    obj.K02_tanulokSzama = this.tanulokSzama;
    obj.K03_tanarokSzama = this.tanarokSzama;
    obj.K04_rendszergazdakSzama = this.rendszergazdakSzama;
    obj.K05_letoltesiSebesseg = this.letoltesiSebesseg;
    obj.K06_szamitogepekSzama = this.szamitogepekSzama;
    obj.K07_lmsEE = this.lmsEE;
    obj.K08_lmsHW = this.lmsHW;
    obj.K09_lmsLAN = this.lmsLAN;

    if (this.lmsLAN) {
      obj.K091_lmsValasztott = this.lmsValasztott;
      obj.K092_lmsHasznalloTanarok = this.kulsoLMSHasznalloTanarok;
    }

    obj.K10_kulsoLMS = this.kulsoLMS;

    if (this.kulsoLMS) {
      obj.K101_kulsoLMSHasznalloTanarok = this.kulsoLMSHasznalloTanarok;
    }

    db.collection("valaszok1") // Elem feltöltése az adatbázisba
      .add(obj)
      .then(docRef => {
        alert(
          `Adatok mentése sikeres!\nRekord azonosítója: ${
            docRef.id
          }\nKöszönöm a kérdőív kitöltését!`
        );
      })
      .catch(error => {
        alert(`Hiba az adatok mentésekor: ${error}`);
        return;
      });

    this.megyek = [];
    this.tanulokSzama = "";
    this.tanarokSzama = "";
    this.rendszergazdakSzama = "";
    this.letoltesiSebesseg = "";
    this.szamitogepekSzama = "";
    this.lmsEE = false;
    this.lmsHW = false;
    this.lmsLAN = false;
    this.lmsValasztott = [];
    this.lmsHasznalloTanarok = "";
    this.kulsoLMS = false;
    this.kulsoLMSHasznalloTanarok = "";
  }
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

.bordered {
  border: 2px solid #a5a5a5;
  border-radius: 4px;
}

.disabledTitle {
  color: rgba(175, 175, 175, 0.5);
}
</style>
