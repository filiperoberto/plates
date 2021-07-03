<template>
  <div class='plate' :class='`plate-${type}`' :class="{'mercosul': mercosul, 'cinza': !mercosul}">
    <span class='header header-mercosul' v-if='mercosul'>
      <span>BRASIL</span>
      <bandeira/>
    </span>
    <span v-else class='header header-cinza'>
      <span class='detalhe-circulo'></span>
      <span class='cidade'>{{uf}} - {{municipio}}</span>
      <span class='detalhe-circulo'></span>
    </span>
    <div class='plate-container' ref='plateContainer'>
      <span>{{letters}}</span>
      <span class='espacamento' v-if='!mercosul && !wrap'>-</span>
      <span>{{numbers}}</span>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import Bandeira from './Bandeira'

export default {
  components: {
    Bandeira
  },
  setup() {
    const plateContainer = ref(null)
    return { plateContainer }
  },
  props: {
    plate: String,
    type: {
      type: String,
      default: 'particular'
    },
    uf: {
      type: String,
      default: 'UF'
    },
    municipio: {
      type: String,
      default: 'municipio'
    }
  },
  computed: {
    letters() {
      return this.plate.slice(0,3)
    },
    numbers() {
      return this.plate.slice(3,8)
    },
    mercosul () {
      return isNaN(parseInt(this.plate.slice(4,5)))
    },
    wrap () {
      if(!this.plateContainer) {
        return;
      }
      const tamanhoFilhos = [...this.plateContainer.children].map(e => e.offsetWidth).reduce((a,b)=> a+b,0)
      const tamanhoPai = this.plateContainer.offsetWidth
      return tamanhoPai < tamanhoFilhos
    }
  }
}
</script>
<style scoped>

  .plate, .plate * {
    box-sizing: border-box;
  }

  .plate {
    width: 100%;
    border-width: 10px;
    border-style: solid;
    border-radius: 7px;
    text-align:center;
  }

  .mercosul.plate-particular {
    border-color: #101c36;
    color: #101c36;
  }

  .mercosul.plate-comercial {
    border-color: #e1422e;
    color: #e1422e;
  }

  .mercosul.plate-especial {
    border-color: #519d3c;
    color:#519d3c;
  }

  .mercosul.plate-oficial {
    border-color: #2d52a0;
    color: #2d52a0;
  }

  .mercosul.plate-colecionador {
    border-color:#818181;
    color:#818181;
  }

  .mercosul.plate-diplomatico {
    border-color: #d09a36;
    color:#d09a36;
  }

  .plate.cinza {
    font-weight:bolder;
  }

  .cinza.plate-particular {
    border-color: #a5a5a5;
    color: #101c36;
    background: #c2c2c2;
  }

  .cinza.plate-comercial {
    border-color:#b23222;
    color:white;
    background:#e1422e;
  }

  .cinza.plate-especial {
    border-color:#3f7c30;
    color:white;
    background:#519d3c;
  }

  .cinza.plate-oficial {
    border-color:#244180;
    background:#2d52a0;
    color:white;
  }

  .cinza.plate-colecionador {
    border-color:#000000;
    background:#1b1b1b;
    color:#c2c2c2;
  }

  .cinza.plate-diplomatico {
    border-color:#c2c2c2;
    color:#b23222;
  }

  .plate-container {
    padding:0.4em;
    letter-spacing: 10px;
    font-size: 50px;
  }

  .cinza .plate-container {
    font-size: 60px
  }

  .plate-container > span {
    display: inline-block;
  }

  .header {
    height:45px;
    margin: 0;
    width:100%;
    position:relative;

    display:flex;
    align-items: center;
    justify-content:center;
  }

  .detalhe-circulo {
    display:inline-block;
    width: 10%;
    height:10px;
    background: gray;
    border-radius: 5px;
    margin-right:10px;
    display:none;
  }

  .header-cinza {
    font-size:20px; 
  }

  .header-mercosul {
    background: #1e4ab3;
    color: white;
  }

  .cidade {
    text-transform:uppercase;
  }
</style>
