<template>
  <ul>
    <li v-for="resource in resources" :key="resource.id">
      <LearningResource
        :title="resource.title"
        :description="resource.description"
        :link="resource.link"
      />
    </li>
  </ul>
</template>

<script>
import LearningResource from '@/components/learning-resources/LearningResource.vue';

export default {
  components: {
    LearningResource,
  },

  props: {
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
</style>
