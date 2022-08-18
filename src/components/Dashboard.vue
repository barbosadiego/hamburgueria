<template>
  <div>
    <div class="burger-table-heading">
      <div class="id">#:</div>
      <div>Cliente:</div>
      <div>Pão:</div>
      <div>Carne:</div>
      <div>Opcionais:</div>
      <div>Ações:</div>
    </div>
    <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
      <div class="order-number">{{ burger.id }}</div>
      <div>{{ burger.nome }}</div>
      <div>{{ burger.pao }}</div>
      <div>{{ burger.carne }}</div>
      <div>
        <ul>
          <li v-for="opcao, index in burger.opcionais" :key="index">
            {{ opcao }}
          </li>
        </ul>
      </div>
      <div>
        <select name="status" class="status">
          <option value="">Selecione</option>
          <option 
            v-for="item in status" 
            :key="item.id" 
            :value="item.tipo"
            :selected="burger.status === item.tipo"
            >
            {{ item.tipo }}
          </option>
        </select>
        <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  data(){
    return{
      burgers: null,
      burger_id: null,
      status: [],
      baseURL: 'http://localhost:3000'
    }
  },
  methods:{
    async getPedidos(){
      const req = await fetch(`${this.baseURL}/burgers`);
      const data = await req.json();
      this.burgers = data;
      this.getStatus();
    },
    async getStatus(){
      const req = await fetch(`${this.baseURL}/status`);
      const data = await req.json();
      this.status = data;
    },
    async deleteBurger(id){
      const req = fetch(`${this.baseURL}/burgers/${id}`,{
        method: 'DELETE'
      });

      this.getPedidos();
    }
  },
  mounted(){
    this.getPedidos();
  }
};
</script>

<style scoped>
.burger-table-heading,
.burger-table-row {
  max-width: 1200px;
  min-width: 1000px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 80px repeat(5, 1fr);
  /* text-align: center; */
  padding: 12px;
  align-items: center;
}
.burger-table-heading{
  font-weight: bold;
  border-bottom: 3px solid #333;
}
.burger-table-row{
  border-bottom: 1px solid #ccc;
}
.delete-btn{
  margin-left: 10px;
  background-color: var(--bg-color);
  color: var(--primary);
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  cursor: pointer;
  transition: .3s;
}
.delete-btn:hover{
  background-color: transparent;
  color: var(--text);
}
li{
  padding: 5px;
}
select{
  padding: 10px;
}
</style>
