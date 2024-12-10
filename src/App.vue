<template>
  <ul>
    <li v-for="resource in storesResources" :key="resource.id">
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
  data() {
    return {
      storesResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org',
        },
      ],
    };
  },
};
</script>
