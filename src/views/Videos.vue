<template>
  <ion-page>
    <ion-content>
      <ion-refresher slot="fixed" @ion-refresh="refresh" id="refresher">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>
      <ion-list id="skeleton" v-if="loading">
        <ion-list-header>
          <ion-skeleton-text animated style="width: 80px"></ion-skeleton-text>
        </ion-list-header>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
        <ion-item>
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h3>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </h3>
            <p>
              <ion-skeleton-text animated style="width: 80%"></ion-skeleton-text>
            </p>
          </ion-label>
        </ion-item>
      </ion-list>
      <ion-list v-else>
        <ion-item v-for="video in videos" :key="video.message">
          <ion-avatar slot="start">
            <ion-skeleton-text></ion-skeleton-text>
          </ion-avatar>
          <ion-label>
            <h2>{{ video.title }}</h2>
            <p>{{ video.description }}</p>
          </ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script>
import {
  IonAvatar,
  IonContent,
  IonItem,
  IonLabel,
  IonList,
  IonListHeader, IonPage,
  IonRefresher,
  IonRefresherContent,
  IonSkeletonText
} from "@ionic/vue";

export default {
  name: "Videos",
  components: {
    IonList,
    IonItem,
    IonListHeader,
    IonAvatar,
    IonLabel,
    IonRefresher,
    IonRefresherContent,
    IonContent,
    IonSkeletonText,
    IonPage,
  },
  data() {
    return {
      videos: [],
      loading: true
    }
  },
  async created() {
    await this.fetchVideos()
    this.loading = false
  },
  mounted() {
    this.refresher = document.getElementById('refresher');
  },
  methods: {
    async refresh() {
      await this.fetchVideos()
      this.refresher.complete()
    },
    async fetchVideos() {
      try {
        this.videos = await this.casteaching.videos()
      } catch (error) {
        console.log(error);
      }
    }
  }
}
</script>

<style scoped>

</style>