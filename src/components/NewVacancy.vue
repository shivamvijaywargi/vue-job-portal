<template>
  <div>
    <div class="box">
      <h1 class="title is-5">Create a vacancy</h1>
      <form @submit.prevent="handleSubmit">
        <input
          required
          v-model="form.title"
          class="input"
          type="text"
          placeholder="Job Title"
        />
        <input
          required
          v-model="form.company"
          class="input"
          type="text"
          placeholder="Company Name"
        />
        <input
          required
          v-model="form.city"
          class="input"
          type="text"
          placeholder="City Name"
        />
        <textarea
          required
          v-model="form.description"
          class="input"
          type="text"
          placeholder="Job Description"
        ></textarea>

        <button class="button is-primary">Post</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        title: '',
        company: '',
        city: '',
        description: '',
      },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit('formSubmit', {
        ...this.form,
        id: new Date().getTime().toString(),
      });

      for (let key in this.form) {
        this.form[key] = '';
      }
    },
  },
};
</script>

<style scoped>
input,
textarea {
  margin-bottom: 20px;
}
</style>
