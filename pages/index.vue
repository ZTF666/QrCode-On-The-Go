<template>
<v-container fluid  >
    <v-main class="dark ">
      <v-container >
        <v-row>


          <v-col cols="12" sm="12"  >
            <v-sheet min-height="70vh" rounded="lg"  >
            <!-- Title -->
              <v-card-title class="jc">
                Generate Your Qr Code !
              </v-card-title>
            <!-- Form -->
              <div class="jc">
                  
                  <v-form ref="form"  lazy-validation >
                  <!-- <v-text-field v-model="text"  label="Text" required class="centered-input" ></v-text-field> -->
                  <v-container fluid>
                    <v-textarea
                    background-color="transparent"
                      name="Text"
                      label="Text"
                      :counter="2953"
                      auto-grow
                      v-model="text"
                    ></v-textarea>
                  </v-container>
                  <div class="buttonHolder">
                  <v-btn  color="purple" rounded  @click="Generate()" class="btp"> Generate </v-btn>
                  </div>
                  </v-form>
                  
              </div>
            <!-- endForm -->
          <!-- Generated QR image code -->
              <v-layout class="d-flex justify-center">
                <v-flex class="d-flex justify-center">
                  <v-card>
                    <center>
                      <v-img
                        class="white--text"
                        height="500px"
                        width="500px"
                        :src="Qr"
                      ></v-img>
                    </center>
                  </v-card>
                </v-flex>
              </v-layout>
          <!-- button layout -->
              <v-layout class="d-flex justify-center mt-10 ">
                <div class="text-xs-center btp">
                  <v-btn rounded color="dark" dark>
                    <button @click="Download()" >
                      <v-icon color="white" class="nls">mdi-content-save</v-icon>
                    </button>
                  </v-btn>
                </div>
              </v-layout>


            </v-sheet>
          </v-col>

        
        </v-row>
      </v-container>
    </v-main>
</v-container>
</template>

<script>
export default {
  head: {
    title: 'Qr code generator',
    meta: [
      {
        hid: 'Qr code generator page',
        name: 'Qr code generator page',
        content: 'Generate a QR code for your links and texts and download it in no time !!',
      },
    ],
  },
data(){
  return{
    text:null,
    Qr:'',
    Api:'https://chart.googleapis.com/chart?cht=qr&chs=500x500&chl=',
    id:'',
  }
},
methods:{
   Generate(){
     if(this.text !=null){
       this.Qr =  this.Api+this.text
        this.text=''
     }
  },
   Download(){
    var FileSaver = require('file-saver')
    // generating random id/name for the picture 
    let characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    for ( var i = 0; i < 12; i++ ) { this.id += characters.charAt(Math.floor(Math.random() * 36)) }
    // initiating download
    FileSaver.saveAs(this.Qr, this.id+".jpg")
}  
}
}
</script>


<style scoped>
/* .up{ margin-top:100px; } */
.jc{ justify-content: center; }
.centered-input >>> input { text-align: center; }
.buttonHolder{ text-align: center; }
.btp{ margin-bottom: 30px; }
.nls{ text-decoration:none; }

</style>