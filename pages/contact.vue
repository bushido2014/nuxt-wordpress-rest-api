<template>
  <div class="container contact-page">
    <ContactForm />
  </div>
</template>
<script>
import ContactForm from '~/components/ContactForm';
export default {
  components: { ContactForm },
  head() {
    return {
      title: 'Contact Page - Nuxt WP',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Website development on a turnkey basis.',
        },
      ],
    };
  },
};
</script>
