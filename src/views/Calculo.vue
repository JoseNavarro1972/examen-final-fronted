<template>
  <div class="calculo-container">
    <h1 class="titulo-centrado">Cálculo de calificaciones</h1>
    <form @submit.prevent="calcular" class="formulario-calculo">
      <div>
        <label for="nota1">Nota 1:</label>
        <input type="number" id="nota1" placeholder="Nota 1" v-model="nota1" min="10" max="70" required>
      </div>
      <div>
        <label for="nota2">Nota 2:</label>
        <input type="number" id="nota2" placeholder="Nota 2"  v-model="nota2" min="10" max="70" required>
      </div>
      <div>
        <label for="nota3">Nota 3:</label>
        <input type="number" id="nota3" placeholder="Nota 3"  v-model="nota3" min="10" max="70" required>
      </div>
      <div>
        <label for="asistencia">Asistencia (%):</label>
        <input type="number" id="asistencia" placeholder="Asistencia"  v-model="asistencia" min="0" max="100" required>
      </div>
      <button type="submit">Calcular</button>
    </form>
    <div v-if="resultado" class="resultado-mensaje">
      <p>{{ resultado.promedio }}</p>
      <p>{{ resultado.estado }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nota1: null,
      nota2: null,
      nota3: null,
      asistencia: null,
      resultado: null
    };
  },
  methods: {
    calcular() {
      if (this.nota1 < 10 || this.nota1 > 70 || this.nota2 < 10 || this.nota2 > 70 || this.nota3 < 10 || this.nota3 > 70) {
        this.resultado = { promedio: 'Las notas deben estar entre 10 y 70.', estado: '' };
        return;
      }
      if (this.asistencia < 0 || this.asistencia > 100) {
        this.resultado = { promedio: 'La asistencia debe estar entre 0 y 100.', estado: '' };
        return;
      }
      const promedio = (this.nota1 * 0.35) + (this.nota2 * 0.35) + (this.nota3 * 0.30);
      if (promedio >= 40 && this.asistencia >= 80) {
        this.resultado = { promedio: `El promedio es: ${promedio.toFixed(2)}`, estado: 'Tu estado es: Aprobado' };
      } else {
        this.resultado = { promedio: `El promedio es: ${promedio.toFixed(2)}`, estado: 'Tu estado es: Reprobado' };
      }
    }
  }
};
</script>

<style scoped>
.calculo-container {
  text-align: center;
}

.titulo-centrado {
  text-align: center;
}

.formulario-calculo {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

.formulario-calculo div {
  margin-bottom: 10px;
}

.formulario-calculo label {
  display: block;
  margin-bottom: 5px;
}

.formulario-calculo input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

.formulario-calculo button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.formulario-calculo button:hover {
  background-color: #0056b3;
}

.resultado-mensaje {
  text-align: center;
  margin-top: 20px;
  font-size: 1.2em;
  color: #333;
}
</style>
