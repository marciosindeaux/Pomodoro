<template>
  <v-container>
    
    <v-row >
      <div class="text-center ma-12">
        <v-progress-circular
          :indeterminate="false"
          :rotate="rotate"
          :size="size"
          :value="value"
          :width="width"
          color="black">

          <v-row v-if="!isPlayed" align="center" justify="center" >
            <v-col cols="12" sm="3">
                <v-text-field
                  v-model="minutos"
                  label="Minutos"
                  required
                ></v-text-field>
            </v-col>
            <v-col cols="12" sm="3">
                <v-text-field
                  v-model="segundos"
                  label="Segundos"
                  :rules="regrasSegundos"
                  required
                ></v-text-field>
            </v-col>
          </v-row>
          <v-row v-else class="big">
              {{minutos}}:{{segundos}}
          </v-row>
        </v-progress-circular>
      </div>
    </v-row>
    <v-row align="center" justify="center">
      <v-btn v-if="!isPlayed" class="mx-2" fab large  @click="iniciaCronometro">
        <v-icon>play_arrow</v-icon>
      </v-btn>
      <v-btn v-else class="mx-2" fab dark large  @click="pararCronometro">
        <v-icon >pause</v-icon>
      </v-btn>
      <v-btn class="mx-2" fab large color="error" @click="zerarCronometro" :disabled="!isPlayed">
        <v-icon >stop</v-icon>
      </v-btn>
    </v-row>
  </v-container>
</template>

<style scoped>
  .big {
    font-size: 60px;
  }
</style>

<script>
  export default {
    name: 'HelloWorld',
    data: () => ({
      regrasSegundos:[ time => time >=0 && time < 60],
      minutos:0,
      segundos:0,
      qtdSegundosTotais:0,
      intervalCron:null,
      isPlayed: false,
      rotate:270,
      value:0,
      width:2,
      size:300
    }),
    methods:{
      iniciaCronometro(){
        let vm = this;
        this.isPlayed = true;
        this.qtdSegundosTotais = (this.minutos*60)+(this.segundos);
        this.intervalCron = window.setInterval(() => {
          if(this.segundos == 0){
            if(this.minutos == 0){
              this.pararCronometro()
            }else{
              this.minutos -= 1;
              this.segundos = 59;
            }
          }else{
            this.segundos-=1;
          }
        }, 1000)
      },
      pararCronometro(){
        if(this.intervalCron){
          this.isPlayed = false;
          this.qtdSegundosTotais = 0;
          window.clearInterval(this.intervalCron);
        }
      },
      zerarCronometro(){
        this.pararCronometro();
        this.minutos = 0 ; 
        this.segundos = 0;
      }
    },
    computed: {
      progress(){
        return (1 - (((this.minutos*60)+(this.segundos))/qtdSegundosTotais))
      }
    }
  }
</script>
