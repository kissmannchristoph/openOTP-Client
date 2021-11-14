<template>
  <ion-segment @ionChange="segmentChanged($event)">
    <ion-segment-button value="friends">
      <ion-label>Friends</ion-label>
    </ion-segment-button>
    <ion-segment-button value="enemies">
      <ion-label>Enemies</ion-label>
    </ion-segment-button>
  </ion-segment>
</template>
<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonButton,
  IonLabel,
  IonSegment
} from "@ionic/vue";
import { defineComponent } from "vue";
import { useRouter } from "vue-router";
export default defineComponent({
  name: "Home",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButton,
    IonLabel,
  IonSegment
  },
  setup() {
    const router = useRouter();
    return { router };
  },
});
</script>