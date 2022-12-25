<template>
  <v-container>
    <v-card 
      class="grey lighten-5" 
      elevation="10"
      >
      <div class="light-blue darken-2 white--text">
        <p>{{ date }}</p>
      </div>
      <v-card-title>{{ title }}</v-card-title>
      <v-card-subtitle>{{ description }}</v-card-subtitle>
      <v-card-actions>
        <v-btn
          class="white--text"
          :style="{ 'background-color': isComplete ? '#616161' : '#039BE5' }"
        >
          <v-icon color="white">mdi-checkbox-marked-circle</v-icon>
          {{ isComplete ? 'Tarea Completa' : 'Tarea Incompleta'}}
        </v-btn>
      </v-card-actions>
      <div class="text-center">
        <v-btn 
          rounded color="black" 
          dark 
          @click="IsDetailsAreVisible = !IsDetailsAreVisible" 
          class="ma-3"
        >
          {{ IsDetailsAreVisible ? "Ocultar detalles" : "Mostrar detalles" }}
        </v-btn>
      </div>
      <v-expand-transition v-show="IsDetailsAreVisible">
      <div v-if="IsDetailsAreVisible">
        <v-card-text>
          <div class="text--primary">
            <h3>Comentarios</h3>
            <div 
              v-for="comment in comments" 
              :key="comment.id"
            >
              <v-icon>mdi-message-reply</v-icon> {{ comment.comment }}
            </div>
          </div>
        </v-card-text>
        <v-card-text>
          <div class="text--primary">
            <h3>Etiquetas</h3>
          </div>
        </v-card-text>
        <v-card-text>
          <v-chip-group
            v-for="tag in tags"
            :key="tag.id"
            v-model="selection"
            active-class="deep-purple accent-4 white--text"
          >
            <v-chip>{{ tag.tag }}</v-chip>
          </v-chip-group>
        </v-card-text>
      </div>
    </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "BaseCard",

  props: {
    date: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    isComplete: {
      type: Boolean,
      required: true,
    },
    comments: {
      type: Array,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    tags: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      IsDetailsAreVisible: false,
    };
  },
};
</script>
