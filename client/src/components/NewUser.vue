<template>
  <div class="registration-holder">
    <form action="#">
      <div class="form-row">
        <input 
          class="form-control"
          type="text"
          placeholder="Your name"
          v-model="newName">
      </div>
      <div class="form-row">
        <input 
          class="form-control"
          type="text"
          placeholder="Your email"
          v-model="newEmail">
      </div>
      <div class="form-row">
        <input 
          class="form-control"
          type="text"
          placeholder="Your password"
          v-model="newPassword">
      </div>
      <input 
        type="submit"
        value="Sign Up"
        @click="signUp()"
        >  
    </form>
  </div>
</template>
<script>
import StoreService from '@/services/StoreService'

export default {
  name: 'NewUser',
  data() {
    return {
      newName: '',
      newEmail: '',
      newPassword: ''
    }
  },
  methods: {
    async signUp() {
      if (this.newName !== '' &&
        this.newEmail !== ''  &&
        this.newPassword !== '' ) {
          const params = {
            userName: this.newName,
            userEmail: this.newEmail,
            userPassword: this.newPassword
          }
          await StoreService.signUp(params)
          this.newName = ''
          this.newEmail = ''
          this.newPassword = ''
      }
    }
  }
}
</script>