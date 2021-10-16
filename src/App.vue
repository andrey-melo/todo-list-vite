<template>
  <h1 class="text-6xl text-center mt-20 mb-20">{{ titulo }}</h1>

  <div class="grid grid-cols-12 lg:grid-cols-3">
    <div
      class="
        space-y-4
        border-2 border-gray-300
        rounded-sm
        p-8
        col-start-2 col-span-10
        lg:col-start-2 lg:col-span-1
      "
    >
      <div>
        <label class="block" for="descricao">Descrição: </label>
        <input
          class="
            border-2 border-gray-300
            outline-none
            rounded-sm
            px-4
            py-2
            focus:border-blue-600
            w-full
          "
          v-model="tarefa.descricao"
          id="descricao"
          type="text"
          placeholder="Digite a descrição da tarefa"
        />
      </div>
      <div>
        <label class="block" for="data">Data: </label>
        <input
          class="
            border-2 border-gray-300
            outline-none
            rounded-sm
            px-4
            py-2
            focus:border-blue-600
            w-full
          "
          v-model="tarefa.data"
          id="data"
          type="date"
        />
      </div>
      <app-btn class="mx-auto" @click="salvar">Salvar</app-btn>
    </div>
  </div>

  <div class="grid grid-cols-12 lg:grid-cols-3 mt-10">
    <div class="border-2 border-gray-300 col-span-10 lg:col-span-1 col-start-2 lg:col-start-2">
      <TabelaTarefas :tarefas="tarefas"></TabelaTarefas>
    </div>
  </div>
</template>



<script>
import TabelaTarefas from "./components/TabelaTarefas.vue";
import AppBtn from "./components/AppBtn.vue";

export default {
  components: {
    TabelaTarefas,
    AppBtn,
  },
  data() {
    return {
      titulo: "Todolist Vite T35",
      tarefa: {},
      tarefas: [],
    };
  },
  methods: {
    salvar() {
      this.tarefas.push(Object.assign({}, this.tarefa)); //Deep Copy
    },
  },
};
</script>

<style>
.riscado {
  text-decoration: line-through;
}
</style>