<template>
  <div>
    <ul v-for="job in jobs" :key="job.id">
      <li class="text-center" id="lista" @click="clickItem(job.name)">
        {{ job.name }}
      </li>
    </ul>

    <div>
      <v-card
        v-if="isOpen"
        class="modal-content"
        @click="isOpen = false"
        color="black"
      >
        <v-card-title>
          <span>{{ name }}</span>
        </v-card-title>
        <v-card-text>
          <ul v-for="(func, indice) in filteredFuncions" :key="indice">
            <li>
              {{ func.funcName }}
            </li>
          </ul>
        </v-card-text>
        <v-card-actions> </v-card-actions>
      </v-card>
    </div>
  </div>
</template>

<script>
import funcDev from "../db/funcoes/developer";
import funcComprador from "../db/funcoes/comprador";
import jobs from "../db/Jobs";
export default {
  data() {
    return {
      isOpen: false,
      jobs,
      name: "",
      funcDev,
      funcComprador,
    };
  },
  computed: {
    filteredFuncions() {
      if (this.name == "DEVELOPER") {
        return this.funcDev;
      } else if (this.name == "COMPRADOR") {
        return this.funcComprador;
      } else {
        return alert("As funções para esse Job ainda estão em andamento!");
      }
    },
  },
  methods: {
    clickItem(item) {
      this.isOpen = true;
      this.name = item;
      console.log(this.name);
    },
  },
};
</script>

<style scoped>
.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

#lista:hover {
  cursor: pointer;
  color: orange;
}
</style>
