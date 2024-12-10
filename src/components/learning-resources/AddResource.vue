<template>
  <BaseCard>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input v-model="title" id="title" name="title" type="text" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          v-model="description"
          id="description"
          name="description"
          rows="3"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input v-model="link" id="link" name="link" type="url" />
      </div>
      <div>
        <BaseButton type="submit">Add Resource</BaseButton>
      </div>
    </form>
  </BaseCard>
  <BaseDialog v-show="!isInputValid" :title="dialogTitle" @close="confirmError">
    <template #default>
      <p>{{ dialogMessage }}</p>
      <p>
        Please check specified field and make sure you enter at least a few
        characters into it.
      </p>
    </template>
    <template #actions>
      <BaseButton @click="confirmError">OK</BaseButton>
    </template>
  </BaseDialog>
</template>

<script>
export default {
  inject: ['addResource'],

  data() {
    return {
      title: '',
      description: '',
      link: '',
      isInputValid: true,
      invalidField: null,
      dialogMessage: '',
    };
  },

  computed: {
    dialogTitle() {
      return `Invalid ${this.invalidField}!`;
    },
  },

  methods: {
    validateFields() {
      if (!this.title.trim()) {
        this.invalidField = 'title';
        return false;
      }

      if (!this.description.trim()) {
        this.invalidField = 'description';
        return false;
      }

      if (!this.link.trim()) {
        this.invalidField = 'link';
        return false;
      }

      return true;
    },

    submitData() {
      this.isInputValid = this.validateFields();

      if (!this.isInputValid) {
        this.dialogMessage = `Please, enter a valid value for ${this.invalidField}!`;
        return;
      } else {
        this.invalidField = null;
        this.dialogMessage = '';
      }

      this.addResource({
        title: this.title,
        description: this.description,
        link: this.link,
      });

      this.title = '';
      this.description = '';
      this.link = '';
    },

    confirmError() {
      this.isInputValid = true;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
  resize: none;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
