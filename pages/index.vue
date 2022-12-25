<template>
  <v-app id="inspire">
    <!--Componente de navegacion y encabezado-->
    <base-bar-navigation
      :completed-tasks="taskCompleteFilter"
      :incompleted-tasks="taskIncompleteFilter"
    >
    </base-bar-navigation>
    <v-main>
      <v-row class="black" md="6" lg="6" xl="6">
        <v-col cols="6" class="shrink">
          <!--Componente para mostrar encabezado de completo-->
          <base-header-task :is-complete="taskIncompleteFilter[2].isComplete" />

          <!--Base card para tareas incompletas-->
          <base-card
            v-for="(task, index) in taskIncompleteFilter"
            :key="index"
            :date="task.date"
            :title="task.title"
            :description="task.description"
            :comments="task.comments"
            :is-complete="task.isComplete"
            :tags="task.tags"
          ></base-card>
        </v-col>
        <v-col cols="6" class="shrink">
          <!--Componente para mostrar encabezado de incompleto-->
          <base-header-task :is-complete="taskCompleteFilter[2].isComplete" />

          <!--Base card para tareas completas-->
          <base-card
            v-for="(task, index) in taskCompleteFilter"
            :key="index"
            :date="task.date"
            :title="task.title"
            :description="task.description"
            :comments="task.comments"
            :is-complete="task.isComplete"
            :tags="task.tags"
          ></base-card>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import BaseCard from "../components/BaseCard.vue";
import BaseBarNavigation from "../components/BaseBarNavigation.vue";
import BaseHeaderTask from "../components/BaseHeaderTask.vue";

export default {
  components: {
    BaseCard,
    BaseBarNavigation,
    BaseHeaderTask,
  },

  data() {

    return {

      taskList: [
        {
          date: "1 de enero del 2023",
          title: "Ir al gimnasio",
          isComplete: false,
          comments: [
            {
              comment: "Llevar agua",
            },
            {
              comment: "Checar mensualidad",
            },
          ],
          description: "gimnasio, toca pierna",
          tags: [
            {
              tag: "Ejercicio",
            },
          ],
        },
        {
          date: "3 de enero del 2023",
          title: "Visitar a mamá",
          isComplete: false,
          comments: [
            {
              comment: "Comprar regalo",
            },
          ],
          description: "Ir a casa de mamá por su cumpleanios",
          tags: [
            {
              tag: "Visita",
            },
          ],
        },
        {
          date: " 6 de enero del 2023",
          title: "Ir al mandado",
          isComplete: false,
          comments: [
            {
              comment: "No olvidar comprar jabon",
            },
          ],
          description: "Crear header para app de restaurant",
          tags: [
            {
              tag: "Compras",
            },
          ],
        },
        {
          date: "14 de diciembre del 2022",
          title: "Create component Header",
          isComplete: true,
          comments: [
            {
              comment: "Usar Vuetify",
            },
          ],
          description: "Crear header para app de restaurant",
          tags: [
            {
              tag: "Programación",
            },
          ],
        },
        {
          date: "13 de diciembre del 2022",
          title: "Ir al gym",
          isComplete: true,
          comments: [
            {
              comment: "Llevar agua",
            },
            {
              comment: "Checar mensualidad",
            },
          ],
          description: "Crear header para app de restaurant",
          tags: [
            {
              tag: "Ejercicio",
            },
          ],
        },
        {
          date: "12 de diciembre del 2022",
          title: "Ir de compras",
          isComplete: true,
          comments: [
            {
              comment: "Llevar agua",
            },
            {
              comment: "Checar mensualidad",
            },
          ],
          description: "Crear header para app de restaurant",
          tags: [
            {
              tag: "Compras",
            },
          ],
        },
        {
          date: "11 de diciembre del 2022",
          title: "Visita al doctor",
          isComplete: true,
          comments: [
            {
              comment: "llevar receta anterior",
            },

          ],
          description: "Ir a cita mensual",
          tags: [
            {
              tag: "Doctor",
            },
          ],
        }
      ],
    };
  },

  //Metodos computados para filtrar tareas por completa o incompleta
  computed: {
    taskCompleteFilter() {
      return this.taskList.filter((task) => task.isComplete === true);
    },
    taskIncompleteFilter() {
      return this.taskList.filter((task) => task.isComplete === false);
    },
  },
};
</script>
