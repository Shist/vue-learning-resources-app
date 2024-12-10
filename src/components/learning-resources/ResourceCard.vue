<template>
  <div>
    <header>
      <h2>{{ title }}</h2>
      <button>Delete</button>
    </header>
    <p>{{ description }}</p>
    <nav>
      <a :href="link" target="_blank">View Resource</a>
    </nav>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
};
</script>
