<template>
  <div class="page">
    <h4>Thêm liên lạc</h4>
    <ContactForm @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import contactService from "@/services/contact.service";
export default {
  components: { ContactForm },
  data() {
    return { message: "" };
  },
  methods: {
    async createContact(data) {
      try {
        await contactService.create(data);
        alert("Liên lạc đã được thêm thành công!");
        this.$router.push({ name: "contactbook" });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
<style scoped>
@import "@/assets/form.css";
</style>
