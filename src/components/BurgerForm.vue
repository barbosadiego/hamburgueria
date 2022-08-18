<template>
  <div>
    <Message :msg="msg"/>
    <form class="burger-form" @submit="createBurger">

      <label for="nome">Nome do Cliente</label>
      <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">

      <label for="pao">Escolha o Pão:</label>
      <select name="pao" id="pao" v-model="pao">
        <option value="">Selecione o pão</option>
        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
      </select>

      <label for="carne">Escolha a Carne:</label>
      <select name="carne" id="carne" v-model="carne">
        <option value="">Selecione a carne</option>
        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
      </select>

      <label class="opcionais-label" for="opcionais">Opcionais</label>
      <div class="opcionais-container">
        <div v-for="item in opcionaisData" :key="item.tipo">
          <input type="checkbox" :name="item.tipo" :id="item.tipo" v-model="opcionais" :value="item.tipo">
          <label  class="checkbox-label" :for="item.tipo">{{ item.tipo }}</label>
        </div>
      </div>
      
      <input type="submit" class="submit-btn" value="Criar meu burguer">

    </form>
  </div>
</template>

<script>
import Message from '@/components/Message.vue'

export default {
  name: 'BurgerForm',
  components:{
    Message,
  },
  data(){
    return{
      paes: null,
      carnes: null,
      opcionaisData: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: 'Solicitado',
      msg: null,
      baseURL: 'http://localhost:3000'
    }
  },
  methods:{
    async getIngredients(){
      const req = await fetch(`${this.baseURL}/ingredientes`);
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisData = data.opcionais;
    },
    async createBurger(e){
      e.preventDefault();

      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado",
      }

      const dataJson = JSON.stringify(data)

      const req = await fetch(`${this.baseURL}/burgers`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: dataJson,
      })

      const res = await req.json();
      this.systemMessage(`Pedido nº ${res.id} solicitado com sucesso!`);
    },
    clearInfo(){
      this.nome = '';
      this.pao = '';
      this.carne = '';
      this.opcionais = '';
    },
    systemMessage(msg){
      this.msg = msg;
      this.clearInfo();

      setTimeout(() => {
        this.msg = '';
      }, 3000)
    }
  },
  mounted(){
    this.getIngredients();
  }
}
</script>

<style scoped>
.burger-form{
  margin: 0 auto;
  max-width: 400px;
  display: grid;
  gap: 10px;
}
label:not(.checkbox-label){
  font-weight: bold;
  margin-top: 15px;
  color: var(--text);
  padding: 5px 10px;
  border-left: 4px solid var(--primary);
}
input, select{
  padding: 5px 10px;
  /* width: 300px; */
}
.opcionais-label{
  margin-bottom: 20px;
}
.opcionais-container{
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.opcionais-container > div{
  display: flex;
  align-items: center;
  gap: 6px;
}
.opcionais-container > div label{
  font-weight: bold;
}
.submit-btn{
  background-color: var(--bg-color);
  color: var(--primary);
  font-weight: bold;
  border: 2px solid var(--bg-color);
  padding: 10px;
  font-size: 1rem;
  margin: 20px auto;
  width: 300px;
  cursor: pointer;
  transition: .3s;
}
.submit-btn:hover{
  background-color: transparent;
  color: var(--text);
}
</style>