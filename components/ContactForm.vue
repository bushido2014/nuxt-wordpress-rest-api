<template>
  <div class="container">
    <h2 class="text-center">Contact</h2>
    <div class="form-wrapper">
      <form @submit.prevent="submitForm">
        <div>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Name"
            required=""
            class="form-control"
          />
        </div>
        <div>
          <input
            type="email"
            id="email"
            name="email"
            v-model="email"
            placeholder="Email"
            required=""
            class="form-control"
          />
        </div>
        <div>
          <textarea
            name="message"
            v-model="message"
            required=""
            class="form-control"
            placeholder="Message"
          ></textarea>
        </div>
        <div>
          <button type="submit">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
const FORMSPARK_ACTION_URL = 'https://submit-form.com/2jzqoBG3';

export default {
  data() {
    return {
      name: '',
      email: '',
      message: '',
    };
  },
  methods: {
    async submitForm() {
      await fetch(FORMSPARK_ACTION_URL, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          Accept: 'application/json',
        },
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          message: this.message,
        }),
      });
      alert('Form submitted');
      this.$router.push('/');
    },
  },
};
</script>
