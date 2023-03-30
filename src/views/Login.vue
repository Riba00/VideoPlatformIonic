<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>Login</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-card>
        <ion-card-header>
          <ion-card-subtitle>Please login</ion-card-subtitle>
        </ion-card-header>

        <ion-card-content>
          <ion-item>
            <ion-label>Email</ion-label>
            <ion-input v-model="email" placeholder="email" type="text"></ion-input>
          </ion-item>

          <ion-item>
            <ion-label>Password</ion-label>
            <ion-input v-model="password" placeholder="password" type="password"></ion-input>
          </ion-item>

          <ion-button @click="login">Login</ion-button>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
import {
  IonButtons,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage,
  IonTitle,
  IonToolbar,
  IonCardHeader,
  IonCardSubtitle,
  IonCardContent,
  IonLabel,
  IonCard,
  IonButton,
  IonItem,
  IonInput
} from "@ionic/vue";
import { Device } from '@capacitor/device';
import store from "../store";

export default {
  name: "Login",
  components: {
    IonButtons,
    IonContent,
    IonHeader,
    IonMenuButton,
    IonPage,
    IonTitle,
    IonToolbar,
    IonCardHeader,
    IonCardSubtitle,
    IonCardContent,
    IonLabel,
    IonCard,
    IonButton,
    IonItem,
    IonInput,

  },
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async login() {
      const info = await Device.getInfo();

      let token = null
      const device_name = (info && info.name) || 'TokenCasteachingIonic'

      try {
        token = await this.casteaching.login(this.email, this.password, device_name)
        this.casteaching.setToken(token)
      }catch (error) {
        console.log(error);
      }

      let user
      try {
        user = await this.casteaching.user()
      }catch (error){
        console.log(error);
      }
      await store.set('token', token)
      await store.set('user', user)

      this.emitter.emit('login', user)

      let path = '/user'

      if (this.$route.params && this.$route.params.wantedRoute) path = this.$route.params.wantedRoute
      this.$router.push({ path })


    }
  }
}
</script>

<style scoped>

</style>