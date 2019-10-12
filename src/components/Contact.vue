<template>
  <div class="container ">
    <h3 class="text-center m-5">We are glad to hear from you</h3>
    <div class="row justify-content-center">
      <form @submit.prevent="submitMessage" class="col-6">
        <div class="form-group">
          <input type="text" class="form-control" name="name" placeholder="Name" v-model="messageForm.name">
        </div>
        <div class="form-group">
          <input type="text" class="form-control" name="amount" placeholder="Amount" v-model="messageForm.amount">
        </div>
        <div class="form-group">
          <textarea class="form-control" name="subject" cols="30" rows="10" v-model="messageForm.subject">Subject</textarea>
        </div>
        <button class="btn btn-primary btn-block" type="submit">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      messageForm: {
        name: "",
        amount: "",
        subject: ""
      }
    };
  },
  methods: {
    submitMessage() {
      // $(e.currentTarget).trigger("reset");

      const { name, amount, subject } = this.messageForm;

      console.log(name, amount, subject);

      this.messageForm = {
        name: "",
        amount: "",
        subject: ""
      };

      // this.messageForm.name = "";
      // this.messageForm.amount = "";
      // this.messageForm.subject = "";
    }
  }
};
</script>