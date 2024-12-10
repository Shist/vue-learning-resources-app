<template>
  <ul>
    <li v-for="resource in resources" :key="resource.id">
      <ResourceCard
        :title="resource.title"
        :description="resource.description"
        :link="resource.link"
      />
    </li>
  </ul>
</template>

<script>
import ResourceCard from '@/components/learning-resources/ResourceCard.vue';

export default {
  components: {
    ResourceCard,
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
