<template>
  <div class="registro-container">
    <h1 class="titulo-centrado">Formulario de registro</h1>
    <form @submit.prevent="validarRegistro" class="formulario-registro">
      <div>
        <label for="nombre">Nombre:</label>
        <input type="text" id="nombre" v-model="nombre" required>
      </div>
      <div>
        <label for="correo">Correo:</label>
        <input type="email" id="correo" v-model="correo" required>
      </div>
      <div>
        <label for="contrasena">Contraseña:</label>
        <input type="password" id="contrasena" v-model="contrasena" required>
      </div>
      <div>
        <label for="repetirContrasena">Repetir Contraseña:</label>
        <input type="password" id="repetirContrasena" v-model="repetirContrasena" required>
      </div>
      <button type="submit">Enviar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      correo: '',
      contrasena: '',
      repetirContrasena: ''
    };
  },
  methods: {
    validarRegistro() {
      if (this.nombre === '') {
        alert('El campo nombre no puede estar vacío.');
        return;
      }
      if (!this.validarCorreo(this.correo)) {
        alert('El formato del correo es incorrecto.');
        return;
      }
      if (this.contrasena === '') {
        alert('El campo contraseña no puede estar vacío.');
        return;
      }
      if (this.contrasena !== this.repetirContrasena) {
        alert('Las contraseñas no coinciden.');
        return;
      }
      alert('El registro se ha realizado correctamente');
    },
    validarCorreo(correo) {
      const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@(([^<>()[\]\.,;:\s@"]+\.)+[^<>()[\]\.,;:\s@"]{2,})$/i;
      return re.test(correo);
    }
  }
};
</script>

<style scoped>
.registro-container {
  text-align: center;
}

.titulo-centrado {
  text-align: center;
}

.formulario-registro {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

.formulario-registro div {
  margin-bottom: 10px;
}

.formulario-registro label {
  display: block;
  margin-bottom: 5px;
}

.formulario-registro input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

.formulario-registro button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.formulario-registro button:hover {
  background-color: #0056b3;
}
</style>
