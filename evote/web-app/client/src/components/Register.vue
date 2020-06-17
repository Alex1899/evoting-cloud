<template>
  <div class="posts">
    <h1>2020 წლის არჩევნები</h1>
    
    <h3>იმ შემთხვევაში თუ რეგისტრირებული არ ხართ, შეავსეთ ქვემოთ მოცემული ფორმა</h3>
    <form v-on:submit="registerVoter">
      <input type="text" v-model="registerData.voterId" placeholder="პირადობის ნომერი">
      <br>
      <br>
      <input type="text" v-model="registerData.firstName" placeholder="სახელი">
      <br>
      <br>
      <input type="text" v-model="registerData.lastName" placeholder="გვარი">
      <br>
      <br>
      <input type="submit" value="რეგისტრაცია">
    </form>
    <br>
    <span v-if="registerReponse">
      <b>{{ registerReponse.data }}</b>
    </span>
    <br>
    <vue-instant-loading-spinner id='loader' ref="Spinner"></vue-instant-loading-spinner>
  </div>
</template>

<script>
import PostsService from "@/services/apiService";
import VueInstantLoadingSpinner from "vue-instant-loading-spinner/src/components/VueInstantLoadingSpinner.vue";

export default {
  name: "response",
  data() {
    return {
      loginData: {},
      registerData: {},
      registerReponse: {
        data: ""
      },
      loginReponse: {
        data: ""
      }
    };
  },
  components: {
    VueInstantLoadingSpinner
  },
  methods: {
    async registerVoter() {

      await this.runSpinner();
      const apiResponse = await PostsService.registerVoter(
        this.registerData.voterId,
        this.registerData.firstName,
        this.registerData.lastName
      );

      console.log(apiResponse);
      this.registerReponse = apiResponse;
      await this.hideSpinner();
    },

    async runSpinner() {
      this.$refs.Spinner.show();
    },
    async hideSpinner() {
      this.$refs.Spinner.hide();
    }
  }
};
</script>
