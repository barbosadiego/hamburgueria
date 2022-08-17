<template>
  <div>
    <p>Componente de Mensagem</p>
    <form class="burger-form">

      <label for="nome">Nome do Cliente</label>
      <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">

      <label for="pao">Escolha o Pão:</label>
      <select name="pao" id="pao" v-model="pao">
        <option value="">Selecione o pão</option>
        <option value="integral">Integral</option>
      </select>

      <label for="carne">Escolha a Carne:</label>
      <select name="carne" id="carne" v-model="carne">
        <option value="">Selecione a carne</option>
        <option value="maminha">Maminha</option>
      </select>

      <label class="opcionais-label" for="opcionais">Opcionais</label>
      <div class="opcionais-container">
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
        <div>
          <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
          <label class="checkbox-label" for="opcionais">Salame</label>
        </div>
      </div>
      
      <input @click.prevent="" type="submit" class="submit-btn" value="Criar meu burguer">

    </form>
  </div>
</template>

<script>
export default {
  name: 'BurgerForm',
  data(){
    return{
      nome: '',
      pao: '',
      carne: '',
      opcionais: '',
    }
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