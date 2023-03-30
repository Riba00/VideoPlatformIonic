<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-card>
        <ion-card-header>
          <ion-card-subtitle>Logout here!</ion-card-subtitle>
        </ion-card-header>
        <ion-card-content>
          <ion-button @click="logout">Logout</ion-button>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
import store from "../store";
import {
  IonButton,
  IonButtons, IonCard, IonCardContent, IonCardHeader, IonCardSubtitle,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage,
  IonToolbar,
} from "@ionic/vue";
export default {
  name: 'Logout',
  components: {
    IonButtons,
    IonContent,
    IonHeader,
    IonMenuButton,
    IonPage,
    IonToolbar,
    IonCardHeader,
    IonCardSubtitle,
    IonCardContent,
    IonButton,
    IonCard,

  },
  methods: {
    async logout () {
      await store.set('token', null)
      const olduser = await store.get('user')
      await store.set('user', null)

      this.emitter.emit('logout', olduser)

      this.$router.push('/login')
    }
  }
}
</script>