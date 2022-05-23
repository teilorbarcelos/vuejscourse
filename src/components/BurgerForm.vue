<template>
  <div>
    <p>componente de mensagem</p>

    <div id="burger-form-container">
      <form id="burger-form">
        <Input label="Nome do cliente:" type="text" id="name" model="name" placeholder="Digite seu nome" />

        <Input label="Escolha o pão:" type="select" id="bread" model="bread" placeholder="Selecione o seu pão"
          :options="breads" />

        <Input label="Escolha a carne do seu burger:" type="select" id="meat" model="meat"
          placeholder="Selecione o tipo de carne" :options="meats" />

        <Input label="Selecione os opcionais:" type="checkbox" id="optionals" name="optionals" model="optionals"
          :options="optionals" />

        <div id="submit-button-container">
          <Button type="submit" label="Criar meu Burger!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Input from "./Input.vue";
import Button from "./Button.vue";

export default {
  name: "BurgerForm",
  components: { Input, Button },
  data() {
    return {
      name: "",
      breads: null,
      meats: null,
      optionals: null
    }
  },
  methods: {
    async getRecipes() {
      const response = await fetch("http://localhost:3000/recipes")
      const data = await response.json()

      this.breads = data.breads
      this.meats = data.meats
      this.optionals = data.optionals
    }
  },
  mounted() {
    this.getRecipes()
  }
}
</script>

<style scoped>
#burger-form-container {
  display: flex;
  justify-content: center;
}

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
