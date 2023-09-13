<template>
  <div>
    <v-container>
      <v-row>
        <v-spacer></v-spacer>
        <v-col>
          <v-img
      src="/ParkingLot.jpg"
    >
  
    </v-img>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
      <v-row>
        <v-spacer></v-spacer>
        <v-col>
          <v-btn-toggle  v-model="toggle_none">
            <v-btn @click="clickedA()">
              <v-icon>mdi-alpha-a</v-icon>
            </v-btn>
  
            <v-btn @click="clickedB()">
              <v-icon>mdi-alpha-b</v-icon>
            </v-btn>
            <v-btn @click="clickedC()">
              <v-icon>mdi-alpha-c</v-icon>
            </v-btn>
  
            <v-btn @click="clickedD()">
              <v-icon>mdi-alpha-d</v-icon>
            </v-btn>
            <v-btn @click="clickedE()">
              <v-icon>mdi-alpha-e</v-icon>
            </v-btn>
  
            <v-btn @click="clickedF()">
              <v-icon>mdi-alpha-f</v-icon>
            </v-btn>
          </v-btn-toggle>
        </v-col>
        <v-spacer></v-spacer>
      </v-row>
    </v-container>
    
 
          
          <v-overlay v-if="showF" >
            <v-container class="accent">
              <v-row>
                <v-col>
                  <v-btn @click="hideF()"> Cancel</v-btn>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="fTopRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="fBottomRow"></horizontalRow>
                </v-col>
              </v-row>
            </v-container>
            

          </v-overlay>
          <v-overlay v-if="showE">
          <v-container class="accent">
            <v-row>
              <v-col >
                <v-btn @click="hideE()"> Cancel</v-btn>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <horizontalRow :spots="eTopRow" ></horizontalRow>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <horizontalRowSmall :spots="eBottomRowL"></horizontalRowSmall>
              </v-col>
              <v-col>
                <v-divider></v-divider>
              </v-col>
              <v-col>
                <horizontalRowMedium :spots="eBottomRowR" ></horizontalRowMedium>
              </v-col>
            </v-row>
            <v-row>
              <v-spacer></v-spacer>
              <v-col class="ml-n12">
                <verticalRow :spots="eLeftVert"></verticalRow>
              </v-col>
              <v-col class="ml-n12">
                <verticalRow :spots="eRightVert"></verticalRow>
              </v-col>
              <v-spacer></v-spacer>
            </v-row>


          </v-container>
          </v-overlay>
          <v-overlay v-if="showA">
            <v-container class="accent">
              <v-row>
                <v-col>
                  <v-btn @click="hideA"> Cancel</v-btn>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="aTopRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="aBottomRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="6">
                  <v-spacer></v-spacer>
                </v-col>
                <v-spacer></v-spacer>
                <v-col>
                  <verticalRow :spots="aColumn"></verticalRow>
                </v-col>
              </v-row>

            </v-container>
          </v-overlay>
          <v-overlay v-if="showB">
            <v-container class="accent">
              <v-row>
                <v-spacer></v-spacer>
                <v-col>
                  <v-btn @click="hideB">Cancel</v-btn>
                </v-col>
                <v-spacer></v-spacer>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="bTopRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="bMidRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <verticalRowScroll :spots="bLeftVert"></verticalRowScroll>
                </v-col> 

                <v-col>
                  <verticalRowScroll :spots="bMidVert"></verticalRowScroll>
                </v-col>

                <v-col>
                  <verticalRowScroll :spots="bRightVert"></verticalRowScroll>
                </v-col> 
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="bBottomRow"></horizontalRow>
                </v-col>
              </v-row>
            </v-container>
          </v-overlay>
          <v-overlay v-if="showC">
            <v-container class="accent">
              <v-row>
                <v-col>
                  <v-btn @click="hideC">
                    Cancel

                  </v-btn>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="cRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row >
                <v-col> 
                  
                  <verticalRowScroll :spots="cLeftVert"></verticalRowScroll>
                
                </v-col>
                <v-col> 
                  
                  <verticalRowScroll :spots="cRightVert"></verticalRowScroll>
                
                </v-col>
              </v-row>
            </v-container>
          </v-overlay>
          <v-overlay v-if="showD">
          <v-container class="accent">
            <v-row>
              <v-col>
                <v-btn @click="hideD">
                cancel
                </v-btn>
              </v-col>
            </v-row>
            <v-row>
            <v-col> 
                  
                  <horizontalRow :spots="dTopRow"></horizontalRow>
                
                </v-col>
               
              </v-row>
              <v-row>
                <v-col>
                  <horizontalRow :spots="dBottomRow"></horizontalRow>
                </v-col>
              </v-row>
              <v-row>
              <v-col>
                <verticalRowScroll :spots="dLeftVert"></verticalRowScroll>
              </v-col>
              <v-col>
                <verticalRowScroll :spots="dRightVert"></verticalRowScroll>
              </v-col>
              </v-row>
            
          </v-container>
          </v-overlay>
  </div>
  </template>
  
  <script>
  import horizontalRow from '../components/horizontalRow.vue'
import VerticalRow from '../components/verticalRow.vue'
import VerticalRowScroll from '../components/verticalRowScroll.vue'
  export default {
    components: { horizontalRow, VerticalRow, VerticalRowScroll },
    data () {
    return {
      bayStatus: "chillin",
      toggle_none: null,
      showF: false,
      showE: false,
      showA: false,
      showB: false,
      showC: false,
      showD: false,
      fTopRow: {
        " 330": ["red", "U"],
        " 329": ["red", "U"],
        " 328": ["red", "U"],
        " 327": ["red", "U"],
        " 326": ["red", "U"],
        " 325": ["red", "U"],
      },
      fBottomRow: {
        " 331": ["red", "U"],
        " 332": ["red", "U"],
        " 333": ["red", "U"],
        " 334": ["red", "U"],
        " 335": ["red", "U"],
        " 336": ["red", "U"],
      },
      eTopRow: {
        " 36": ["red", "U"],
        " 35": ["red", "U"],
        " 34": ["red", "U"],
        " 33": ["red", "U"],
        " 32": ["red", "C"],
        " 31": ["red", "C"],
        " 30": ["red", "C"],
        " 29": ["red", "C"],
        " 28": ["red", "C"],
        " 27": ["red", "C"],
        " 26": ["red", "C"],
        " 25": ["red", "C"],
        " 24": ["red", "C"],
        " 23": ["red", "C"],
        " 22": ["red", "U"],
        " 21": ["red", "U"],
        " 20": ["red", "U"],
        " 19": ["red", "U"],
        " 18": ["red", "U"],
        " 17": ["red", "U"],
        " 16": ["red", "U"],
        " 15": ["red", "U"],
        " 14": ["red", "U"],
        " 13": ["red", "U"],
        " 12": ["red", "U"],
        " 11": ["red", "U"],
        " 10": ["red","U"],
        
      },
      eBottomRowR: {
        " 59": ["red", "U"],
        " 60": ["red", "U"],
        " 61": ["red", "U"],
        " 62": ["red", "U"],
        " 63": ["red", "U"],
        " 64": ["red", "U"],
        " 65": ["red", "U"],
        " 66": ["red", "U"],
        " 67": ["red", "U"],
        " 68": ["red", "U"],
        " 69": ["red", "U"],
        " 70": ["red", "U"],
        " 71": ["red", "U"],
        " 72": ["red", "U"],
        " 73": ["red", "U"],
        " 74": ["green", "U"],
        " 75": ["green", "U"],
        " 76": ["green", "U"]
      },
      eBottomRowL: {
        " 37": ["red", "U"],
        " 38": ["red", "U"],
        " 39": ["red", "U"],
        " 40": ["red", "U"],
        " 41": ["red", "U"],

      },
      eLeftVert: {
        " 42": ["red", "U"],
        " 43": ["red", "U"],
        " 44": ["red", "U"],
        " 45": ["red", "U"],
        " 46": ["red", "U"],
        " 47": ["red", "U"],
      },
      eRightVert: {
        " 58": ["red", "U"],
        " 57": ["red", "U"],
        " 56": ["red", "U"],
        " 55": ["red", "U"],
        " 54": ["red", "U"],
        " 53": ["red", "U"],
        " 52": ["green", "U"],
      },
      aTopRow: {
        " 219": ["red", "U"],
        " 220": ["red", "U"],
        " 221": ["red", "U"],
        " 222": ["red", "U"],
        " 223": ["red", "U"],
        " 224": ["red", "U"],
        " 225": ["red", "U"],
        " 226": ["red", "U"],
        " 227": ["red", "U"],
        " 228": ["red", "U"],
        " 229": ["red", "U"],
        " 230": ["green", "U"],
        " 231": ["red", "U"],
        " 232": ["red", "U"],
        " 233": ["red", "U"],
        " 234": ["red", "C"],
        " 235": ["red", "C"],
        " 236": ["red", "C"],
        " 237": ["red", "C"],
        " 238": ["red", "C"],
        " 239": ["red", "C"],
        " 240": ["red", "C"],
        " 241": ["red", "C"],

      },
      aBottomRow: {
        " 400": ["red", "U"],
        " 401": ["red", "U"],
        " 402": ["red", "U"],
        " 403": ["red", "U"],
        " 218": ["red", "U"],
        " 217": ["red", "U"],
        " 216": ["red", "U"],
        " 215": ["red", "U"],
        " 214": ["red", "U"],
        " 213": ["red", "U"],
        " 212": ["green", "U"],
        " 211": ["red", "U"],
        " 210": ["red", "U"],
        " 209": ["red", "U"],
        " 208": ["red", "U"],
        " 207": ["red", "U"],
        " 206": ["red", "U"],
        " 205": ["red", "U"],
        " 204": ["red", "U"],
        " 203": ["red", "U"],
        " 202": ["red", "U"],
      },
      aColumn: {
        "201": ["red", "U"],
        "200": ["red", "U"],
        "199": ["red", "U"],
        "198": ["red", "U"],
        "197": ["red", "U"],
        "196": ["red", "U"],
        "195": ["red", "U"],
        "194": ["red", "U"],
        "193": ["red", "U"],
      },
      bLeftVert: {
        "181": ["red", "U"],
        "182": ["red", "U"],
        "183": ["red", "U"],
        "184": ["red", "U"],
        "185": ["red", "U"],
        "186": ["red", "U"],
        "187": ["red", "U"],
        "188": ["red", "U"],
        "189": ["red", "U"],
        "190": ["red", "U"],
        "191": ["red", "U"],
        "192": ["red", "U"],
      },
      bTopRow: {
        " 241": ["red", "C"],
        " 242": ["red", "C"],
        " 243": ["red", "C"],
        " 244": ["red", "C"],
        " 245": ["red", "C"],
        " 246": ["red", "C"],
        " 247": ["red", "C"],
        " 248": ["red", "C"],
        " 249": ["red", "C"],
        " 250": ["red", "C"],
        " 251": ["red", "C"],
        " 252": ["red", "C"],
        " 253": ["red", "C"],
        " 254": ["red", "C"],
        " 255": ["red", "C"],
        " 256": ["red", "C"],
        " 257": ["red", "C"],
        " 258": ["red", "C"],
        " 259": ["red", "C"],
        " 260": ["red", "U"],
        " 261": ["green", "U"],
        " 262": ["red", "U"],
        " 263": ["red", "U"],
        " 264": ["red", "U"],
        " 265": ["red", "U"],
        " 266": ["green", "U"],
        " 267": ["green", "U"],
        " 268": ["green", "U"],
        " 269": ["green", "U"],
      },
      bMidRow: {
        " 180": ["red", "U"],
        " 179": ["red", "U"],
        " 178": ["red", "U"],
        " 177": ["green", "U"],
        " 176": ["red", "U"],
        " 175": ["red", "U"],
        " 174": ["green", "U"],
        " 173": ["green", "U"],
        " 172": ["red", "U"],
        " 171": ["green", "U"],
        " 170": ["green", "U"],
        " 169": ["green", "U"],
        " 168": ["green", "U"],
        " 167": ["green", "U"],
        " 166": ["red", "U"],
        " 165": ["green", "U"],
        " 164": ["green", "U"],
        " 163": ["green", "U"],
        " 162": ["green", "U"],
        " 161": ["red", "U"],
      },
      bBottomRow: {
        " 320": ["red", "U"],
        " 131": ["red", "U"],
        " 132": ["red", "U"],
        " 133": ["red", "U"],
        " 134": ["red", "U"],
        " 135": ["red", "U"],
        " 136": ["red", "U"],
        " 137": ["red", "U"],
        " 138": ["green", "U"],
        " 139": ["red", "U"],
      },
      bMidVert: {
        " 160": ["red", "U"],
        " 159": ["green", "U"],
        " 158": ["green", "U"],
        " 157": ["green", "U"],
        " 156": ["red", "U"],
        " 155": ["green", "U"],
        " 154": ["red", "U"],
        " 153": ["green", "U"],
        " 152": ["green", "U"],
        " 151": ["green", "U"],
        " 150": ["green", "U"],
        " 149": ["red", "U"],
        " 148": ["green", "U"],
        " 147": ["red", "U"],
        " 146": ["red", "U"],
        " 145": ["red", "U"],
        " 144": ["red", "U"],
        " 143": ["red", "U"],
        " 142": ["green", "U"],
        " 141": ["green", "U"],
        " 140": ["red", "U"],
      }, 
      bRightVert: {
        " 270": ["red", "U"],
        " 271": ["green", "U"],
        " 272": ["green", "U"],
        " 273": ["green", "U"],
        " 274": ["green", "U"],
        " 275": ["green", "U"],
        " 276": ["green", "U"],
        " 277": ["green", "U"],
        " 278": ["green", "U"],
        " 279": ["green", "U"],
        " 280": ["green", "U"],
        " 281": ["green", "U"],
        " 282": ["green", "U"],
        " 283": ["red", "C"],
        " 284": ["red", "C"],
        " 285": ["red", "C"],
        " 286": ["red", "C"],
        " 287": ["red", "C"],
        " 288": ["red", "C"],
        " 289": ["red", "C"],
        " 290": ["red", "C"],
        " 291": ["red", "C"],
        " 292": ["red", "C"],
        " 293": ["red", "C"],
        " 294": ["red", "C"],
        " 295": ["red", "U"],
        " 296": ["green", "U"],
        " 297": ["red", "U"],
        " 298": ["green", "U"],

      },
      cRow: {
        " 319": ["red", "U"],
        " 130": ["red", "U"],
        " 129": ["red", "U"],
        " 128": ["red", "U"],
        " 127": ["red", "U"],
        " 126": ["red", "U"],
        " 125": ["red", "U"],
        " 124": ["red", "U"],
        " 123": ["red", "U"],
        " 122": ["red", "U"],
      },
      cLeftVert: {
        " 121": ["red", "U"],
        " 120": ["red", "U"],
        " 119": ["green", "U"],
        " 118": ["red", "U"],
        " 117": ["red", "U"],
        " 116": ["red", "U"],
        " 115": ["red", "U"],
        " 114": ["red", "U"],
        " 113": ["red", "U"],
        " 112": ["red", "U"],
        " 111": ["red", "U"],
        " 110": ["red", "U"],
        " 109": ["red", "U"],
        " 108": ["red", "U"],
        " 107": ["red", "U"],
        " 106": ["red", "U"],
        " 105": ["red", "U"],
        " 104": ["red", "U"],

      },
      cRightVert: {
        " 299": ["red", "U"],
        " 300": ["red", "U"],
        " 301": ["red", "U"],
        " 302": ["green", "U"],
        " 303": ["green", "U"],
        " 304": ["red", "U"],
        " 305": ["green", "U"],
        " 306": ["green", "U"],
        " 307": ["red", "U"],
        " 308": ["green", "U"],
        " 309": ["green", "U"],
        " 310": ["green", "U"],
        " 311": ["green", "U"],
        " 312": ["red", "U"],
        " 313": ["green", "U"],
        " 314": ["green", "U"],
        " 315": ["red", "U"],
        " 316": ["red", "U"],
        " 317": ["red", "U"],
        " 318": ["red", "U"],

      },
      dTopRow: {
        " 01": ["green", "U"],
        " 02": ["red", "U"],
        " 03": ["red", "U"],
        
      },
      dBottomRow: {
        " 97": ["green", "U"],
        " 98": ["red", "U"],
        " 99": ["red", "U"],
        " 100": ["red", "U"],
        " 101": ["red", "U"],
        
      }, 
      dLeftVert: {
        " 77": ["green", "U"],
        " 78": ["green", "U"],
        " 79": ["green", "U"],
        " 80": ["green", "U"],
        " 81": ["green", "U"],
        " 82": ["green", "U"],
        " 83": ["green", "U"],
        " 84": ["green", "U"],
        " 85": ["green", "U"],
        " 86": ["green", "U"],
        " 87": ["green", "U"],
      },
      dRightVert: {
        " 96": ["red", "U"],
        " 95": ["red", "U"],
        " 94": ["green", "U"],
        " 93": ["red", "U"],
        " 92": ["green", "U"],
        " 91": ["green", "U"],
        " 90": ["green", "U"],
        " 89": ["green", "U"],
        " 88": ["green", "U"],
      }

    }
  },
  methods: {
    
    clickedF() {
      this.showF = true
    },
    clickedE() {
      this.showE = true
    },
    clickedD() {
      this.showD = true
    },
    clickedC() {
      this.showC = true
    },
    clickedB() {
      this.showB = true
    },
    clickedA() {
      this.showA = true
    },
    hideF(){
      this.showF = false
    },
    hideE(){
      this.showE = false
    },
    hideD(){
      this.showD = false
    },
    hideC(){
      this.showC = false
    },
    hideB(){
      this.showB = false
    },
    hideA(){
      this.showA = false
    }
  }
  }
  </script>
  