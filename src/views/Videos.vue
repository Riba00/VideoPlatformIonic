<template>
  <ion-page>
    <ion-list id="skeleton">
      <ion-list-header>
        <!--      <ion-skeleton-text animated style="width: 80px"></ion-skeleton-text>-->
        Videos
      </ion-list-header>
      <ion-item v-for="video in videos" :key="video.message">
        <ion-avatar slot="start">
          <!--        <ion-skeleton-text></ion-skeleton-text>-->
        </ion-avatar>
        <ion-label>
          <h2>{{ video.title }}</h2>
          <p>{{ video.description }}</p>
        </ion-label>
      </ion-item>
    </ion-list>
  </ion-page>

</template>

<script>
import {IonAvatar, IonItem, IonLabel, IonList, IonListHeader, IonPage} from "@ionic/vue";
import casteaching from "@acacha/casteaching";

const api = casteaching({baseUrl:'http://casteachingriba.test/api/'})

export default {
  name: "Videos",
  components: {
    IonList,
    IonItem,
    IonListHeader,
    IonAvatar,
    IonLabel,
    IonPage,
  },
  data(){
    return {
      videos: []
    }
  },
  async created() {
    this.videos = await api.videos()
  }
}
</script>

<style scoped>

</style>