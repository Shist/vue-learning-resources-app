<template>
  <ul>
    <li v-for="resource in resources" :key="resource.id">
      <LearningResource
        :id="resource.id"
        :title="resource.title"
        :description="resource.description"
        :link="resource.link"
      />
    </li>
  </ul>
  <p v-if="!resources.length">No stored resources. Please add some.</p>
</template>

<script>
import LearningResource from '@/components/learning-resources/LearningResource.vue';

export default {
  components: {
    LearningResource,
  },

  inject: {
    resources: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}

p {
  text-align: center;
  font-size: 1.5rem;
}
</style>
