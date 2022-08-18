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
    <div class="burger-table-row">
      <div class="order-number">1</div>
      <div>João</div>
      <div>Pão de Trigo</div>
      <div>Maminha</div>
      <div>
        <ul>
          <li>Salame</li>
          <li>Tomate</li>
        </ul>
      </div>
      <div>
        <select name="status" class="status">
          <option value="">Selecione</option>
          <option value="producao">Em produção</option>
        </select>
        <button class="delete-btn">Cancelar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',
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
  text-align: center;
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
