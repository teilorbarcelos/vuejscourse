<template>
  <div>
    <p>componente de mensagem</p>

    <div>
      <form id="burger-form">
        <Input label="Nome do cliente:" type="text" id="name" model="name" placeholder="Digite seu nome" />

        <Input label="Escolha o pão:" type="select" id="bread" model="bread" placeholder="Selecione o seu pão"
          :options="breads" />

        <Input label="Escolha a carne do seu burger:" type="select" id="meat" model="meat"
          placeholder="Selecione o tipo de carne" :options="meats" />

        <Input label="Selecione os opcionais:" type="checkbox" id="options" name="options" model="options"
          :options="options" />

        <div id="submit-button-container">
          <Button type="submit" label="Criar meu Burger!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import Input from "./Input.vue";
import Button from "./Button.vue";

export default {
  name: "BurgerForm",
  components: { Input, Button },
  data() {
    return {
      name: "",
      breads: [{ value: 'integral', label: 'Integral' }],
      meats: [{ value: 'maminha', label: 'Maminha' }],
      options: [
        { value: 'salame', label: 'Salame' },
        { value: 'cebola', label: 'Cebola' },
        { value: 'alho', label: 'Alho' }
      ]
    }
  }
}
</script>

<style scoped>
#burger-form {
  width: max-content;
  max-width: 400px;
  margin: 0 auto;
}

#submit-button-container {
  display: flex;
  justify-content: center;
}
</style>
