<template>
  <v-container>
    <v-card elevation="5">
      <v-card-title
        :style="{ 'background-color': IsComplete ? '#616161' : '#039BE5' }"
        class="white--text">{{ IsComplete ? 'Completos' : "En progreso" }}</v-card-title
      >
    </v-card>
  </v-container>
</template>


<script>
export default {
  name: 'BaseHeaderTask',
  
  props: {
    IsComplete: {
      type: Boolean,
      required: true,
    },
  },
};
</script>