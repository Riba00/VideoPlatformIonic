<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>User</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">User</ion-title>
        </ion-toolbar>
      </ion-header>


      <div>
        <ion-avatar>
          <img alt="Silhouette of a person's head" src="https://ionicframework.com/docs/img/demos/avatar.svg" />
        </ion-avatar>
        <h1>User</h1>
        <p>Name: {{ this.user && this.user.name}}</p>
        <p>Email: {{ this.user && this.user.email}}</p>

      </div>
    </ion-content>
  </ion-page>

</template>

<script>
import {
  IonAvatar,
  IonButtons,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage, IonTitle, IonToolbar
} from "@ionic/vue";
import store from "../store";

export default {
  name: "User",
  components: {
    IonButtons,
    IonContent,
    IonHeader,
    IonMenuButton,
    IonPage,
    IonTitle,
    IonToolbar,
    IonAvatar
  },
  data() {
    return {
      user: {}
    }
  },
  async mounted() {
    this.user = await store.get('user')
  }
}
</script>

<style scoped>

</style>