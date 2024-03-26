<template>
    <div class="page">
      <h4>Thêm Liên hệ</h4>
      <ContactForm
        :contact="contact"
        @submit:contact="addContact"
      />
      <p>{{ message }}</p>
    </div>
  </template>
  <script>
  import ContactForm from "@/components/ContactForm.vue";
  import ContactService from "@/services/contact.service";
  export default {
    components: {
      ContactForm,
    },
    
    data() {
      return {
        contact: {
            name: "",
            email:"",
            address:"",
            phone: "",
            
        },
        message: "",
      };
    },
    methods: {
      async addContact(data) {
        try {
          await ContactService.create(data);
          this.message = "Thêm Liên hệ thành công.";
        } catch (error) {
          console.log(error);
        }
      },
      
    },
    created() {
      this.message = "";
    },
  };
  </script>