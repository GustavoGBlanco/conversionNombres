<template>
  <div class="container">
    <h1>{{ titulo }}</h1>
    <p>
      Es una guia de estilos que podemos encontrar en cualquier lenguaje que nos
      ayuda a la legibilidad de nuestro código para palabras compuestas o frase.
    </p>
    <h2>Frase</h2>
    <input
      type="text"
      v-model="frase"
      placeholder="Por favor escriba una frase"
    />
    <h2>camelCase</h2>
    <span>{{ camelCase || "camelCase" }}</span>
    <h2>PascalCase</h2>
    <span class="capitalize">{{ camelCase || "PascalCase" }}</span>
    <h2>snake_case</h2>
    <span>{{ snake_case || "snake_case" }}</span>
    <h2>kebab-case</h2>
    <span>{{ kebakcase || "kebab-case" }}</span>
  </div>
</template>

<script>
export default {
  props: ["titulo"],
  data() {
    return {
      frase: "",
    };
  },
  computed: {
    camelCase() {
      var expReg = /\s/g;
      let coincidencias = [];
      let conversionCamelCase = "";
      let copiaFrase = [...this.frase.toLowerCase()];

      while (expReg.exec(this.frase) !== null) {
        coincidencias.push(expReg.lastIndex);
      }

      coincidencias.forEach((indiceCoincidencia) => {
        if (copiaFrase[indiceCoincidencia] !== undefined) {
          copiaFrase[indiceCoincidencia] = copiaFrase[
            indiceCoincidencia
          ].toUpperCase();
        }
      });

      conversionCamelCase = copiaFrase.join("").replace(expReg, "");

      return conversionCamelCase;
    },
    snake_case() {
      var expReg = /\s/g;
      return this.frase.toLowerCase().trim().replace(expReg, "_");
    },
    kebakcase() {
      var expReg = /\s/g;
      return this.frase.toLowerCase().trim().replace(expReg, "-");
    },
  },
};
</script>

<style scoped>
p {
  margin-bottom: 5%;
}
input {
  display: block;
  width: 100%;
  padding: 0.375rem;
  font-size: 1rem;
  line-height: 1.5;
  color: #495057;
  background-color: #f5f5f5;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  text-align: center;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
.container {
  left: 20%;
  right: 20%;
  position: fixed;
  padding: 20px;
  border-radius: 0.25rem;
  background-color: white;
  box-shadow: 5px 10px #888888;
}
.capitalize {
  text-transform: capitalize;
}
</style>
